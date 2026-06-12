---
title: "Have to install XP over Lucid"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by ray field on 2011-03-04
This is about the last thing I wanted to do unfortunately I have to install XP on this box for one single program -- I would use a VM except it's a proprietary image editing SW and I think would be very fussy.

1) Can I use KDE Partition Manager to create a new primary partition at the end of my hard disk and then install XP to that? Or would that violate some XP restriction?  Here's  fdisk -l:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4982

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       60801   488384001    5  Extended
/dev/sda5           59579       60801     9823716   82  Linux swap / Solaris
/dev/sda6               1        1148     9221215+  83  Linux
/dev/sda7            1149       27895   214845246   83  Linux
/dev/sda8           27896       44916   136721151   83  Linux
/dev/sda9           44917       59578   117772483+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7ffe4391

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb4a71e64

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    c  W95 FAT32 (LBA)
```

2) If the above is possible, is there a way to be sure that XP actually goes into that partition?  I'm afraid of the XP install routine just wiping the whole disk clean.

3) I know that 'doze will bugger grub, so I'm prepared to use the LiveCD to repair grub. a la 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

I can't remember, however, how I would add Windoze to the grub menu.

---

### Post by grahammechanical on 2011-03-04
According to that listing you have three hard discs sda, sdb, sdc. Am I correct? It looks like you have a disc formatted as FAT32 . If you do indeed have three hard discs, could you not physically remove the other two or at least the hard disc with Ubuntu on? Then when you install XP you will not do anything to the Ubuntu hard disc.

Even if I have misread the partition information, you should know this. When you restore Grub by running update grub or update grub2 it will find all the operating systems on all the discs that are installed in the machine. It will add your Windows installation to the Grub menu.

Regards.

---

### Post by ray field on 2011-03-04
oops -- the latter two hard disks are external USB drives (I wish I could install XP to one of them).

some of my main concerns: 1) the number of primary drives -- I think there are only two here, but I can't tell from fdisk, and 2) whether I can boot from a new primary at the end of the HDD and 3) how I'll be able to identify that new primary partition from inside Windows' installation routine....

---

### Post by ray field on 2011-03-04
yeah, it looks like a fecal low-pressure system waiting to happen, I'll see what Capture NX looks like in Virtualbox.

---

