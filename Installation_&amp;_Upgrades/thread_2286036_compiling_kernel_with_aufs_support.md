---
title: "compiling kernel with aufs support?"
date: 2015-07-09
forum: Installation &amp; Upgrades
---

### Post by spano2 on 2015-07-09
i've been working on compiling aufs support into the kernel but i can't seem to find good instructions on how to do this. i've tried upgrading the kernel to 4.0 and patching it, i've tried downgrading the kernel and patching it. i always run into some sort of problem because there really are no good instructions on this that i can find. does anyone know where i can find a fairly detailed guide on how to accomplish this? i'm using ubuntu 15.04 with kernel version 3.19.0-15-generic. thank you in advance for any help!

-spano

---

### Post by tgalati4 on 2015-07-09
I couldn't find any tutorials on [aufs]("http://http://www.thegeekstuff.com/2013/05/linux-aufs/"), but have you tried running it in userland with *aufs-tools* and using the debug symbols to see if there are problems in userland first?

> tgalati4@Mint17 ~ $ apt-cache search aufs-tools
aufs-tools - Tools to manage aufs filesystems
aufs-tools-dbg - Tools to manage aufs filesystems (debug)



Also I noticed there is [ausf4]("http://aufs.sourceforge.net/") for 4.X kernels and aufs3 for 3.X kernels.  Have you tried both sets of source code?

What specific errors are you having?  Where is the patch or the kernel-compile failing?

Normally, when you can't find a guide, you have to write one.  So let's start.  What specific steps have you taken?

---

### Post by v3.xx on 2015-07-10
You may find this thread interesting.

[http://ubuntuforums.org/showthread.php?t=2285690](http://ubuntuforums.org/showthread.php?t=2285690)

---

### Post by James_Ryan_Stortz on 2015-07-11
*post deleted by author.*

---

