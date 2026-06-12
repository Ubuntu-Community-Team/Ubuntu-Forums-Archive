---
title: "How to Install utorrent from source code?"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by rootnet47 on 2011-05-14
Hi! I'm new to linux and I'm using ubuntu 10.10 since it relished. I've download utorrent-server-3.0-25053.tar.gz. I tried to install it using steps describe bellow,

tar zxf filename.tar.gz
moved to the dir that has been created after extract

now
./configure

after hitting enter message shown as "./configure no such file"

I've configured intltool-0.41.1.tar.gz and libgraph-1.0.1.tar.gz using that very command installed them successfully.

Can anybody help me to install utorrent?

---

### Post by kronick on 2011-05-14
I am not an expert, but i would say you can't because utorrent was build for windows.

---

### Post by rootnet47 on 2011-05-14
yes, but it is also available for linux based OS.

check this out
[http://www.utorrent.com/downloads](http://www.utorrent.com/downloads)

---

### Post by kronick on 2011-06-21
ok, first of all sorry for not replying to you sooner.

Here is the deal, that is not source code, so u don't need to compile it. Here is what u do:

1. extract the archive 
2. double click file named *utserver*
3. go to firefox(or whatever browser u r using) and type in the address:
```
http://localhost:8080/gui/
```
default username is ***admin***, leave password empty.

Hope you get this, and again sorry for not replying sooner.

---

