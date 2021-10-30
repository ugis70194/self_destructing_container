# 自壊するdockerコンテナ

## きっかけ
<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">docker.socketをマウントしてコンテナ内外のdockerコマンドの結果を同じにするやつ怖すぎる</p>&mdash; Niuez (@xiuez) <a href="https://twitter.com/xiuez/status/1453619716145090562?ref_src=twsrc%5Etfw">October 28, 2021</a></blockquote>
これ遊べそうじゃない？

## 概要
`docker-compose up`すると`exited with code 137 (SIGKILL)`で終了する

## 解説
しません(今は気が向かないので)  
- [コンテナからコンテナを操作する - 二畳半堂](https://blog.nijohando.jp/post/docker-in-docker-docker-outside-of-docker/)
- [Dockerコンテナ内からDockerを使うことについて](https://esakat.github.io/esakat-blog/posts/docker-in-docker/)
このあたりを参照するとコンテナ内からコンテナを操作する方法について理解できるはず  
あとは`grep`と`awk`で自分のコンテナIDを取得して`cat`で受け取ってshに渡して終わり

## メモ
- `cat`は引数なしで使うと標準入力から入力を受け取るらしい
- `$()`ってするとカッコの中身をシェルに渡すらしい
- なので`docker rm -f $(cat)`みたいに標準入力から受け取った値を引数として取れるらしい
- [catを使った小技](https://qiita.com/okuramasafumi/items/022e48106ba73ddaa579)