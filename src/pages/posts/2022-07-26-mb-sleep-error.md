---
layout: ../../layouts/MarkdownPostLayout.astro
title: 'MacBookのスリープ復帰に失敗する問題'
pubDate: 2022-07-26
description: ''
tags: ["Mac"] 
icon: "💻"
---

## MacBook Airで発生した問題

端的に言うと、**スリープから再開しようとMacBook Airのフタを開いた時に、強制再起動みたいな挙動をする**ことです。

![MacOS Booting Screen](../../assets/images/mac/macos-startup-apple-logo-progress-bar.png)

2018年製のIntel MacBook Airで発生しました。

## 対処法

Redditで同様の問題を報告している投稿では、以下のようにすることで解決していたので紹介します。

標準の「ターミナル.app」で以下のコマンドを入力。

```shell
sudo pmset -a standby 0
```

このコマンドを実行してパスワードを入力すると、確かにスリープが正常に動作するようになりました。

欠点は、若干バッテリーの減りが早くなるそうです。

## 原因?

解決法のコメントの書かれた投稿はこちらです。

[Sleep wake failure in EFI - Reddit](https://www.reddit.com/r/MacOS/comments/dme38s/sleep_wake_failure_in_efi/)

> MacBook Air 2018がスリープから復帰するときや、今回のように復帰しないときに、このエラーが結構な頻度で出ます。bridgeOSのカーネルパニックが起きていて、ロジックボードを交換してもらった修理歴があります。ソフトウェアの問題だと思うのですが、何かご指摘があればお願いします。smcとnvをリセットしました。また、怪しいソフトウェアなどはインストールしていません。 Microsoft Office、itsycalなどいくつか入れていますが、エラーはフレッシュインストールかどうかに関係なく起こるようです。


どうやら**修理歴があると発生する問題**のようです。確かに、私の場合もTouch IDが反応しなくなって、マザーボードごと交換してもらったことがあります。

これが直接関係しているのかわかりませんが、一つの原因になっている可能性もあります。

結局はっきりした原因はわからず、完全に修正する方法は今のところ見つけていないので、とりあえず上記のコマンドを実行するしか方法はなさそうでした。