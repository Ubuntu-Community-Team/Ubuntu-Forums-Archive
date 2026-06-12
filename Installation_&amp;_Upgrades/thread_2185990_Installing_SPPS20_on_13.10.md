---
title: "Installing SPPS20 on 13.10"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by lanetherif on 2013-11-05
Hi,

I am trying to install SPSS 20 and none of the three interfaces for installation works. I've followed the steps in another thread and installed ```
libstdc++5
``` and ```
lib32z1 lib32ncurses5 lib32bz2-1.0
``` as they have replaced ```
ia32-libs
``` Then, I wrote down ```
sudo ln -s /lib/x86_64-linux-gnu/libc.so.6 /lib/libc.so.6
``` It didn't work and I still can't use any of the interfaces, namely that GUI, Console and Silent.

Any ideas?

---

### Post by lanetherif on 2013-11-11
Bump!

---

### Post by lanetherif on 2013-11-12
Ok, it turned out to be related to ia32-libs which turned out to be removed in 13.10. I have added the Raring repository via Synaptic and installed ia32-libs. With it, came 200 mb of other files. Hopefully, it won't break another part of system. :D

SPSS installs now.

---

### Post by mithun6 on 2014-07-18
i need to install SPSS on my ubuntu 14.04 please help

---

