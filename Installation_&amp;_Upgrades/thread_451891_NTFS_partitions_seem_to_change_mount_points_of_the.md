---
title: "NTFS partitions seem to change mount points of their own accord"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by VMOS on 2007-05-22
This is kinda complex to explain but please bear with me, hopefully it'll make sense in the end
I have 5 drives in my system, 1 dvd, 3 ide HDD and 1 sata on a pci card, it was primarily a windows xp system and I installed ubuntu with no real hassle, all drive and partitions were detected ok, when I run sudo  fdisk I get this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4863    39062016    7  HPFS/NTFS
/dev/sda2            4864        5500     5116702+   c  W95 FAT32 (LBA)
/dev/sda3   *        5501        8050    20482875    6  FAT16
/dev/sda4            8051        9729    13486567+   f  W95 Ext'd (LBA)
/dev/sda5            8051        9729    13486536    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7689    61761861    7  HPFS/NTFS
/dev/sdb2   *        7690        9638    15655342+  83  Linux
/dev/sdb3            9639        9729      730957+   5  Extended
/dev/sdb5            9639        9729      730926   82  Linux swap / Solaris

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19122   153597433+   7  HPFS/NTFS
/dev/sdc2           19123       29321    81923467+   7  HPFS/NTFS
/dev/sdc3           29322       38913    77047740    7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161    7  HPFS/NTFS




yes I've got a lot of partitions, but have a look at my fstab



proc /proc proc defaults 0 0
# Entry for /dev/sdc2 :
UUID=003d3efa-59c0-4e6d-9482-2077f1821647 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=84095d95-b708-4bd9-a8ad-1394d2302e51 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sdc1 /media/bigdrive\040A ntfs-3g defaults,locale=en_IE.UTF-8 0 0
/dev/sdb1 /media/Video ntfs-3g defaults,locale=en_IE.UTF-8 0 0
/dev/sda1 /media/Programs ntfs-3g defaults,locale=en_IE.UTF-8 0 0
/dev/sdd1 /media/Music ntfs-3g defaults,locale=en_IE.UTF-8 0 0
/dev/sdd2 /media/Downloads ntfs-3g defaults,locale=en_IE.UTF-8 0 0
/dev/sdd3 /media/Pictures ntfs-3g defaults,locale=en_IE.UTF-8 0 0

so what's the problem? well for example the one that's listed as SDD1 on fdisk (that's my 80g sata drive)  was SDA1 before I rebooted, SDC1 matches on fdisk and fstab but SDC2 and 3 on fdisk were SDD 2 and 3 on fstab but because they're now SDC they're not listed on fstab and so aren't mounted
now I can go in and edit the table and get them mounted (usually in read only mode though) but it'll change again once I reboot. 
two things, I'm not 100% certain if it's every time I reboot, it's certainly every time I boot into windows and then back to ubuntu 
if I use the NTFS configuration tool I'll get a non-specific error message when I try to mount SDA5, SDC2 and SDC3 (as they are listed in fdisk)

any suggestions?

---

### Post by VMOS on 2007-05-23
Anyone even heard of this or am I going mad?

---

