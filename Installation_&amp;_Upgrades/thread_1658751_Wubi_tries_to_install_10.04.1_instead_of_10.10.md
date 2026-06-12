---
title: "Wubi tries to install 10.04.1 instead of 10.10"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by Sail323 on 2011-01-03
I downloaded the latest version of Wubi and the Ubuntu 10.10 Desktop ISO and have them in the same folder on a Windows XP, SP3 laptop.

When I run Wubi, it starts to download 10.04.1 not 10.10.  How do I fix this?

---

### Post by Bucky Ball on 2011-01-03
Easiest way? Just install from the 10.10 ISO (make a cd and boot from it). There will be an icon somewhere on the desktop or option to install Ubuntu there. You will need to make some free space for it on your disk.

When it gets to the partitioning section choose to manually partition and just leave the Windows NTFS partition alone (it will be clearly visible in there).

Three basic partitions are best:

/ = Where the OS lives.
/home = where your data lives.
/swap (2Gb) = the Linux equivalent of a Windows 'pagefile'.

These names you will find as defaults. You can add any other partitions you like. Choose EXT4 as your file format (/swap with choose its own).

---

