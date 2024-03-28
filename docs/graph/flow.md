本页面主要介绍网络流相关的基本知识。

## 概述

网络（network）是指一个特殊的有向图 $G=(V,E)$，其与一般有向图的不同之处在于有容量和源汇点。

-   $E$ 中的每条边 $(u, v)$ 都有一个被称为容量（capacity）的权值，记作 $c(u, v)$。当 $(u,v)\notin E$ 时，可以假定 $c(u,v)=0$。

-   $V$ 中有两个特殊的点：源点（source）$s$ 和汇点（sink）$t$（$s \neq t$）。

对于网络 $G=(V, E)$，流（flow）是一个从边集 $E$ 到整数集或实数集的函数，其满足以下性质。

1.  容量限制：对于每条边，流经该边的流量不得超过该边的容量，即 $0 \leq f(u,v) \leq c(u,v)$；
2.  流守恒性：除源汇点外，任意结点 $u$ 的净流量为 $0$。其中，我们定义 $u$ 的净流量为 $f(u) = \sum_{x \in V} f(u, x) - \sum_{x \in V} f(x, u)$。

对于网络 $G = (V, E)$ 和其上的流 $f$，我们定义 $f$ 的流量 $|f|$ 为 $s$ 的净流量 $f(s)$。作为流守恒性的推论，这也等于 $t$ 的净流量的相反数 $-f(t)$。

对于网络 $G = (V, E)$，如果 $\{S, T\}$ 是 $V$ 的划分（即 $S \cup T = V$ 且 $S \cap T = \varnothing$），且满足 $s \in S, t \in T$，则我们称 $\{S, T\}$ 是 $G$ 的一个 $s$-$t$ 割（cut）。我们定义 $s$-$t$ 割 $\{S, T\}$ 的容量为 $||S, T|| = \sum_{u \in S} \sum_{v \in T} c(u, v)$。

## 常见问题

常见的网络流问题包括但不限于以下类型问题。

-   最大流问题：对于网络 $G = (V, E)$，给每条边指定流量，得到合适的流 $f$，使得 $f$ 的流量尽可能大。此时我们称 $f$ 是 $G$ 的最大流。
-   最小割问题：对于网络 $G = (V, E)$，找到合适的 $s$-$t$ 割 $\{S, T\}$，使得 $\{S, T\}$ 的容量尽可能小。此时我们称 $\{S, T\}$ 是 $G$ 的最小割。
-   最小费用最大流问题：在网络 $G = (V, E)$ 上，对每条边给定一个权值 $w(u, v)$，称为费用（cost），含义是单位流量通过 $(u, v)$ 所花费的代价。对于 $G$ 所有可能的最大流，我们称其中总费用最小的一者为最小费用最大流。

我们将在稍后的章节中对它们进行详细介绍。

## 例题：网络流 24 题

网络流 24 题是中文互联网上广泛流传的一个题单（[LibreOJ](https://loj.ac/problems/tag/30)/[洛谷](https://www.luogu.com.cn/problem/list?tag=332)），至少在 2010 年前后就已经存在。该题单引入了一些经典的将其他问题建模为网络流问题的技巧。由于时代的局限性，这些问题未必是最具代表性的网络流问题，但仍值得有志于算法竞赛的读者一阅。