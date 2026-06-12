---
title: "How to clone Ubuntu installation from 80GB HDD to 500GB HDD?!"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by HX_unbanned on 2010-12-27
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024754

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9965    80040960    6  FAT16

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f009

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9328    74920960   83  Linux
/dev/sdb2            9328        9730     3227649    5  Extended
/dev/sdb5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x998ecb72

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdd: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       10011    80413326    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f009

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9328    74920960   83  Linux
/dev/sde2            9328        9730     3227649    5  Extended
/dev/sde5            9328        9730     3227648   82  Linux swap / Solaris

Disk /dev/sdf: 260 MB, 260046848 bytes
16 heads, 32 sectors/track, 992 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2750274f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         992      253936    6  FAT16

---

Disk **/dev/sde** is my **new** 500GB Hitachi SATA2 NCQ 16MB Cache Hard Disk Drive.
Disk **/dev/sdb** is my **old** 80GB HDD with Ubuntu on it.

I have followed this tutorial: [http://www.linux.com/archive/feed/152592](http://www.linux.com/archive/feed/152592)

Result is this ( after proceeding with 
> $ sudo ddrescue -v /dev/sdb /dev/sde command ): 

#1
[IMG]http://img813.imageshack.us/img813/9043/screenshotla.png[/IMG]
#2:
[IMG]http://img573.imageshack.us/img573/6338/screenshot1bss.png[/IMG]

Why it is this way? Also - I suddenly have lost 44,35 GB of HDD space?! Why? Hitachi HDD is runn9ing on my PC for first time in its life and already making headaches ... ](*,):-k:cry:

NOTES:
- I did execute this command from installed Ubuntu Desktop, not form LiveCD / LiveUSB / etc.
- I did not manage to resize these partitions as tutorial above claimed.
- **Pictures above are made from _Lucid Lynx LiveCD_ because Maverick LiveCD got damaged and it cannot boot anymore ...**

--

Could you provide step-by-step guide how to correctly clone Ubuntu to my new 500GB HDD?

Thanks. Help is very urgent and extremely appreciated.

---

### Post by dino99 on 2010-12-27
plenty examples & howtos around on google :)

here is one of them:

[http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)

---

