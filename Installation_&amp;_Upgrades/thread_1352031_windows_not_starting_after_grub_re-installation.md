---
title: "windows not starting after grub re-installation"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by shivchal on 2009-12-11
Hi everybody.
Hardware : 
HP Dv2000 laptop with Dual Core 1 GB Ram; 150GB HDD SATA.

Software : 
Vista &  Ubuntu 9.10 - Dual boot on different partitions on a same hard disk 
/dev/sda1   *           1        7444    59785897    7  HPFS/NTFS
/dev/sda2            7444       12182    38065986+   f  W95 Ext'd (LBA)
/dev/sda3           12183       18722    52529652+   7  HPFS/NTFS
/dev/sda4           18722       19457     5904384    7  HPFS/NTFS
/dev/sda5            7444        7705     2104483+  82  Linux swap / Solaris
/dev/sda6            7706        7954     2000061   82  Linux swap / Solaris
/dev/sda7            7955        9199    10000431   83  Linux
/dev/sda8            9200       12182    23960916   83  Linux

Problem :
Windows vista not loading after grub Installation.

Problem detail:
First I had Vista only. For obvious reasons I wanted to move to Ubuntu. I first installed Ubuntu 8.04 & had been installing higer versions, until Ubuntu 9.10. Recently my Vista was totally not recoverable. So I re-installed Vista over the same windows Vista partition. After that I had to re-install grub, to access linux. I re-installed it & I could login to my previously installed Ubuntu. But when I try to boot to my Vista it says.

"error : no such device : 14e01aa6e01a8e5c
Press any key to continue..."

The grub.cfg file is the same that was there before the second vista installation. 
My sincere thanks in advance for all the help.

Cheers!
Arun

---

### Post by jpeddicord on 2009-12-13
Moved to Installation & Upgrades. (not a tutorial)

---

### Post by darkod on 2009-12-13
> **shivchal said:**
> 

"error : no such device : 14e01aa6e01a8e5c
Press any key to continue..."



That's the UUID of the old vista partition I guess. When you reformated the partition it got new UUID. Depending if you are running grub1 (comes with 9.04 and before) or grub2 (with 9.10), you need to use:
sudo update-grub

for grub2. For grub1 go into /boot/grub/menu.lst and see where to change the UUID with the new one. You will find the new UUID with:
sudo blkid

---

### Post by shivchal on 2009-12-14
Hi Darkod
It worked ! Thanks a lot.

Shivchal

---

