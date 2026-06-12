---
title: "problems with the GRUB"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by jjleonb on 2010-06-10
Hi! this is the problem: I have Ubuntu Server 8.04 and everything is working properly with it.  The problem is that I had to install WINXP in another hard drive.  Now in the grub, the only option that I have is my ubuntu server.  How do I reinstall it correctly, I mean the GRUB, when I run my CD, I don't know the steps for reinstalling from it, or if I have to do from another way.  With Fdisk -l these are the options: 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          36      289138+  83  Linux
/dev/sda3              37       19457   155999182+   5  Extended
/dev/sda5             280        1495     9767488+  83  Linux
/dev/sda6              37         279     1951834+  82  Linux swap / Solaris
/dev/sda7            1496        3927    19535008+  83  Linux
/dev/sda8           18242       19457     9767488+  83  Linux
/dev/sda9            3928        5143     9767488+  83  Linux
/dev/sda10           5144       18241   105209653+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 10.2 GB, 10204766208 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa49ea49e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1239     9952236    7  HPFS/NTFS

---

### Post by darkod on 2010-06-10
You don't need to reinstall anything. 8.04 is using grub1 which needs menu.lst to be manually edited to add entry for XP. The file is /boot/grub/menu.lst

The entry added at bottom should look something like:

title Windows XP
rootnoverify (hd1,0)
makeactive
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

The two map commands (lines) might need to be switched, I'm not sure.

---

