---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by mariourk on 2007-10-10
I'm having trouble booting my freshly installed ubuntu 7.04 installation. I get the error message you see in the title of the thread. I've searched for this error and found plenty of threads. However, none of them offers a solution that words for me. Ubuntu 7.10 beta gives this error when I try to boot the livecd.

I think the problem is with the chipset driver. The chipset of my laptop is sis 900. Somehow it seems to load the wrong drivers and them gives errors on libata. Therefore it doesn't reconise the harddrive and says that /dev/hda2 does not exist.

I'm used to Gentoo. With Gentoo, I would have build a kernel myself, to solve this. But I have no idea how to do this the Ubuntu way. I hope someone can help me to fix this thing.

Thanks a lot anyway :D

---

### Post by wpshooter on 2007-10-12
Assuming that there is nothing on the computer that you need to save/keep, have you tried WIPING the hard drive completely clean with killdisk and then tried the installation again ?

[www.killdisk.com](www.killdisk.com)

---

