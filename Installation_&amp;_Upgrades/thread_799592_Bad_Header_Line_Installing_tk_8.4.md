---
title: "Bad Header Line Installing tk 8.4"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by randal on 2008-05-19
Hello.

I'm trying to install Erlang on Gutsy. It needs tk 8.4 but when I try to install I get this (below is with --fix-missing).

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  erlang-base erlang-dev erlang-examples erlang-mode erlang-nox erlang-src erlang-x11 tcl8.4 tk8.4
Suggested packages:
  erlang-manpages erlang-doc-html tclreadline
The following NEW packages will be installed:
  erlang erlang-base erlang-dev erlang-examples erlang-mode erlang-nox erlang-src erlang-x11 tcl8.4 tk8.4
0 upgraded, 10 newly installed, 0 to remove and 39 not upgraded.
Need to get 11.4MB/38.4MB of archives.
After unpacking 108MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://cache](http://cache) gutsy/main tcl8.4 8.4.15-1build1 [1169kB]
Err [http://cache](http://cache) gutsy/main tk8.4 8.4.15-1ubuntu1
  Bad header line
Err [http://cache](http://cache) gutsy/universe erlang-x11 1:11.b.5dfsg-2ubuntu1
  Bad header line
Err [http://cache](http://cache) gutsy/universe erlang-dev 1:11.b.5dfsg-2ubuntu1
  Bad header line
0% [Waiting for headers]

I hope someone could help me on this. Thanks.

---

### Post by randal on 2008-05-22
I think the problem was with **[http://cache](http://cache)** part.

---

