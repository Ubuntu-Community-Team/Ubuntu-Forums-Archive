---
title: "Alternate CD install/Partition table not showing"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by carpex on 2007-04-20
Hi, I am trying to install Feisty x64 from the alternate cd. When I get to the partitioning part, I select the manual option. Where it is supposed to display all my current partition table I just have my hard drive (SCSI 120 GB..sda) with no partition information. I should have a series of partitions with Vista and my previous Ubuntu (i386). Shouldn't these show up there? I am afraid to click on the hard drive and write a new partition table as I really want to keep Vista on there.

Thanks for the help!

GL

---

### Post by carpex on 2007-04-20
Hi, I just tried this using the normal livecd install of Feisty x64 and my partition table is still not showing up! GParted shows my complete hard drive as "unallocated". I should have at least 6 partitions on there... 

My Vista and Feisty 32 bits are booting ok. 

Here is the output of fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14333       14594     2096128    c  W95 FAT32 (LBA)
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313        8203    55346176    7  HPFS/NTFS
/dev/sda4            8204       14594    51328700    f  W95 Ext'd (LBA)
/dev/sda5           14333       14594     2096128   dd  Unknown
/dev/sda6   *        8204       14079    47198938+  83  Linux
/dev/sda7           14080       14332     2032191   82  Linux swap / Solaris


Any help would be appreciated.

GL

---

### Post by BruceBerry on 2007-04-21
I have the same problem with the kubuntu live cd and a dell inspiron 6400 :-(

---

### Post by sigg.switz on 2007-04-21
I am also unable to see my partitions....what is going on? I have a dell d600 with XP

---

### Post by monti on 2007-05-25
You can probably work around your problem by using TestDisk, look here: [http://ubuntuforums.org/showthread.php?p=2486121#post2486121](http://ubuntuforums.org/showthread.php?p=2486121#post2486121) 

The bug is located in gparted's subsystem, libparted: [http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14](http://parted.alioth.debian.org/cgi-bin/trac.cgi/ticket/14)

---

