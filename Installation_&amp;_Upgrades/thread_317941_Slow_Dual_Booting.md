---
title: "Slow Dual Booting"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by crazyarlo on 2006-12-13
I have installed Edgy on a Dell C400 laptop with XP already on it.  I just tried to use the built in dynamic partitioning, to save time, and it worked great! Wireless, everything! 

The only problem is that after Grub comes up, selecting Ubuntu results in extended boot up time ... up to 120 seconds.  Could this be caused by the partitioning setup?  Do I need to install XP on it's own partition (I need it for work), and THEN install Ubuntu on it's own partition?  

Dell C400
1.2 Ghz. Pentium III 
512 Megs Ram
30 Gig Hard Drive
Truemobile 802.11b PC card wireless card

Any thoughts?

Arlen Owens

---

### Post by bulldog on 2006-12-13
If the installation went well,you should have Windows and Ubuntu on different partitions.
Windows uses NTFS or FAT32 and Ubuntu ext3.

The boot-delay can have many reasons,from a slow hard-disk till not recognized hardware.

---

