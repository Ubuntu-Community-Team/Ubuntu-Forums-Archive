---
title: "grub error 22 please help me."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by vissu on 2007-10-21
im in serious problem... while installing ubuntu 7.04 with the help of wubi, it has not detected iso file. i tried to install with help of cd, i have gone to command line install and installed linux(i dunno abt this). got confused and recovered partitions. now it says "loading grub... error 22" please tell me how to recover from this error:(

---

### Post by Sef on 2007-10-21
> 22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

Sounds like your GRUB is messed up.  I would download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/") and use that to install GRUB.   It has easy to follow instructions.

---

