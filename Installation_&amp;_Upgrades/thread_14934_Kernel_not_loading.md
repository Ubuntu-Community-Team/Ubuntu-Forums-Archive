---
title: "Kernel not loading"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by BurningShed on 2005-02-10
Hello,
I have a secondary computer that I am trying to install Ubuntu on, unfortunatly the installer hangs while trying to load the kernel from the CD, I moved the HD to this computer, installed ubuntu, (almost) everything worked fine, so i tried moving the HD back to the other machine but it ran into problems loading the kernel.

the specs of the machine are:
(everything but the HD came with the machine)
Dell Dimension 166Mz Pentium
65 Mbs of SDRAM
13gb western digital caviar EIDE HD set to single

the errors are:
(booting onto the previous Ubuntu Install, both in recuse mode and regular)
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
Kernel panic: VFS: unable to mount root fs on unknown-block(0,0)

(Install CD (both before and after HD transfer)
(right after detecting hardware to find CD-Rom drives)
user.notice cdrom-detect: searching for Ubuntu installlation media...
[long message mostly in hex, and a call trace that ends at start_kernel+0x193/0x197
Code: 0f 0b eb 03 e1 4d 8c c4 89 0a 89 82 e4 00 00 00 a1 80 91 28
Kernel Panic: fatal exception in interrupt
In interrupt handler - not syncing

I'm brand new to Ubuntu (and Linux in general, this is my first distro (mostly becuase they sent me the CDs) and so far I really like Ubuntu, and Linux in general, i've had only a few problems (other than this one) so far and i have been able to fix them with the help of the FAQs and this forum.  any help or advice on this problem would be greatly appreicated,

Thanks
Robby

---

### Post by BurningShed on 2005-02-10
also, I have tried just about all the boot options on the boot CD (although not booting from the HD, becuase i don't know how, or even if its possible) and its warty, not hoary.

---

