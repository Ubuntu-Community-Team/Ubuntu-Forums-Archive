---
title: "doesn't show distinct partition of ubuntu and windows"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2010-01-09
Hi all,
I want to adjust the size allocated to my windows partition but on opening gparted i realised that there was no different partition for my ubuntu there. The only patition i have is the windows showing which takes all but i have ubuntu installed on my system and it was not installed on wubi.
What could be the problem?
Anytime i attempt shrinking it from the live-cd mode it complains about lossing all the data on that partition.
How can i seperate the linux partition from the windows ?

---

### Post by vinnywright on 2010-01-09
mabey 2 drives ....Gparted onley showes 1 at a time ......upper rite corner of screen has the box to switch drives

be carfull resising a NTFS partition you should clear out as mutch junk as posabell then run chkdsk then defrag and chkdsk agin then use the older ver of gparted as the newest has a prob with NTFS read this

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

if you start ubuntu and do 
> sudo fdisk -lwhat do you see .......post it.

VINNY

---

### Post by zukario on 2010-01-09
I think also there are two drives it where the problems comes.

---

### Post by 10ghost on 2010-01-09
I checked the top right corner and threre was only one drive there.
I issued the command *sudo fdisk -l*
and the output was

[I]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30075       30402     2620416    c  W95 FAT32 (LBA)
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       29749   228407295+   7  HPFS/NTFS
/dev/sda4           29750       30402     5238503    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6           29750       30053     2441848+  83  Linux
/dev/sda7           30054       30074      168651   82  Linux swap / Solaris

Partition table entries are not in disk order[/I]

I hope this would guide you better.
Thanks for the first response.

---

