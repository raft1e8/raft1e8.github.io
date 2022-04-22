---
layout: page
title: "Mo's algorithm"
permalink: https://raft1e8.github.io/Pages/Tech/Mo
---

[HOME]("https://raft1e8.github.io) > [TECH]("https://raft1e8.github.io/Pages/Tech.html") > [Mo's alogrithm]("https://raft1e8.github.io/Pages/Tech/Mo.html")

# Mo's algorithm 

#### 利用場面
- 区間クエリが与えられる
    - 区間更新がない
- セグメント木では処理できない
    - ２つの範囲の結果を結合できない場合
        - s.t. $ f[l,m) + f[m,r]) \neq f[l,r) $
- 範囲を1つずつ伸縮できる
- クエリ先読み可能
    - インタラクティブな問題では使用不可

#### 計算量オーダー
$ O(K(Q+N)\sqrt{N}) $

#### 実装
ABC242G「Range Pairing Query」用の実装

***solve()*** :クエリを追加しきった後実行
***add(), del()*** :範囲を追加,削除
***insert()*** :クエリを追加

ほかの問題で利用する場合はadd(),del(),処理するためのデータ型を書き換える[^1]
[^1]:いつかtemplateで様々なデータ型に対応させる

```C++11
insert:query 配列にpairで範囲を突っ込む[l,r)
solve():query配列をソートしてans配列生成
add(),del():solve()内で呼び出される
query,ans,data配列を持つ
整数型としてクエリの数、値の最大値、最小値を持っておく(平方分割のため)
```
