---
title: "Help needed - wubi installer wrong cpu name (x86_64 instead of i686)"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by vur246 on 2008-06-01
Hi all !

I've just install ubuntu using wubi installer on my Dell XPS 410 WinXP
Installation is fine, the problem is that 

uname -m shows cpu as x86_64
and obviously gcc compiler and all other tools also configured for x86_64.

It causes me problem since I have my own scripts/apps which works only with i686.

Sysinfo shows cpu as

GenuineIntel
Intel(R) Core(TM)2 CPU 6600 @ 2.40

Is it any way to install using wubi enforcing i686 cpu ?

Thanks a lot

As a trial I installed Ubunty under vmware fusion on my other computer with the identical cpu, this time by using DVD image for ubunty i686 and cpu info is i686 so everything is worked. I didn't find any options for Wubi to choose the cpu type

---

