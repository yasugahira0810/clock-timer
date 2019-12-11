# 20191205

- [vue-jsテストハンドブック](https://lmiller1990.github.io/vue-testing-handbook/ja/#vue-jsテストハンドブック)
- msgの受け渡しがよくわからない
- Home.vueからも、App.vueからもHelloWorld.vueを呼び出しているように見える。なぜ？
  - わかった。vue.jsインストール時点では、Vue RouterがHome.vueからHelloWorld.vueを呼び出していた。その後、Vuetifyをインポートした時点で、そこが上書きされ、App.vueからHelloWorld.vueが呼ばれるようになった。設定が反映されないように見えたのは、キャッシュの影響と思われる。
- とりあえずテストは通ってコンパイルもできるけど、なんで動いているのかわからない状態
  - 解決
- lintのときのwarningがうざいのはなんとかならないか

# 20191206

- [Vue.jsで時計を作ってみる(2)](https://techtutor.ddns.net/wp/?p=199)

  - ここパクって時計を動かした。

- 時計の時間、分、秒の３つを持たせて描画して、この３つはread-onlyにすれば良さそう。それに加えてタイマー用の分をもたせられれば良さそう。できるのか？

  - 時間、分、秒を一つの時計として見せたり、時間の幅を表示するのが難しそう。そもそもpickerなので時計として表示できないこと自体は普通で、こちらが変な使い方しようとしていた気がする。

- ## Vuetifyのv-time-picker使うのはやめる。

- [Vue Clock2](https://bestvist.github.io/vue-clock2/docs/)を試してみる。こちらの方が柔軟性ありそう。

- 一回フォルダの中身を全消しして、vue createからやり直して良さそう。VuetifyとかVue Routerとか使わなそうだからいらないもの一掃したい。

# 20191209

- これまでのファイル変更を取り消して改めて開発を進めるため、過去のcommitに戻して作業してcommitしてgit pushしたところ、エラーが出た。

```bash
MacBook-Air-3:clock-timer anhirayuuta$ git push origin master
To https://github.com/yasugahira0810/clock-timer.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/yasugahira0810/clock-timer.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

これgit pullすると前のファイル変更を取り込んでしまいそうだったので、git push -fした。

これやるとファイルはこちらの変更が入って、commit履歴的にはこれまでのものに続いた形になると思ったが、履歴も消えてしまった。memo.mdだけは取っておいたので直近は困らないが、この動きは覚えておく。