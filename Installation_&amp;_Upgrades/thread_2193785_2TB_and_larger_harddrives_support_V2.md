---
title: "2TB and larger harddrives support? V2"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by xerces8 on 2013-12-14
As [the old thread]("http://ubuntuforums.org/showthread.php?t=1657961") is closed, I continue here.

> **xerces8 said:**
> 
Hi!

With 2TB and 3TB drives available, how is the support from the Ubuntu side?

Anyone tried?
Developers?

Regards,
David 

I just tested Ubuntu 13.10 x64 in a VirtualBox v4.3.4 virtual PC and:
 - it installs
 - hangs at boot

It drops into a grub rescue shell, with error: attempt to read or write outside of disk 'hd0'

I also tried Fedora 19 and it works fine, so I compared the partitioning and the reason is obvious:
 - Fedora uses a /boot partition
 - Ubuntu creates one big root filesystem partition

So I reinstall and instead of automatic partitioning I changed the existing partitions (the leftover of the first installation) manually:
 - removed /
 - add a 1GB /boot partition
 - re-add / after the /boot parition

This way it works fine.

Not sure where exactly the bug lies.

PS: Windows 8 also works, but uses MBR/MSDOS partitioning and creates a 2TB partition (and one small boot partition, Windows calls is "System" partition).

---

