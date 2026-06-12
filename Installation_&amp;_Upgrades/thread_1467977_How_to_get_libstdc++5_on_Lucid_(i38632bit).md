---
title: "How to get libstdc++5 on Lucid (i386/32bit) ?"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Relaxed_Trader on 2010-05-01
Hi Group,

today I made the jump from Jaunty to Lucid - only to discover that the libstdc++5 libraries and tools are no longer in the repository.
Since my dev tools still rely on libstdc++5, I need a way to get these installed on 10.04 (i386/32bit).  Where can I get these?  What repository should I add to Synaptic?

Thanks!

Relaxed_Trader

---

### Post by Daimonan on 2011-10-28
I'm going to bump this, since I'm running in to a similar issue even now when I use some older software that requires libstdc++5.  

Anybody know how to install these older libraries?  Will their presence interfere with the operation of programs using libstdc++6?

---

### Post by deloquencia on 2011-10-28
Just install it manually with dpkg in a terminal without any repository.

Check [http://packages.ubuntu.com/oneiric/i386/libstdc++5/download](http://packages.ubuntu.com/oneiric/i386/libstdc++5/download) - choose a mirror and download it.

When you're running on a 64-bit processor, go this way: [http://packages.ubuntu.com/oneiric/amd64/libstdc++5/download](http://packages.ubuntu.com/oneiric/amd64/libstdc++5/download)

In the terminal install it with:
**sudo dpkg -i *<package>***

---

