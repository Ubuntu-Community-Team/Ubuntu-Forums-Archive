---
title: "Installed Ubuntu 10.10 on a primary partition on a RAID 0 HD and Grub is not loading"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by chroncile on 2011-04-16
i installed Ubuntu 10.10 on a new, primary partition on a RAID 0 hard drive. I partitioned the RAID 0 HD and that's where I got the primary partition to install Ubuntu. Grub is installed on Ubuntu, but it's not loading when I start up my computer; it goes to the Windows 7 boot menu and boots Windows 7. There is no Ubuntu listed.

I did an fdisk -l. Ignore sda10, that's not my current linux partition; it's my old linux partition from a separate HDD.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x343f37e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5272    42347308+   7  HPFS/NTFS
/dev/sda2           48020       48641     4996215    7  HPFS/NTFS
/dev/sda3            5273       48019   343365247    f  W95 Ext'd (LBA)
/dev/sda5            5273        7833    20571201    7  HPFS/NTFS
/dev/sda6            7834       10510    21502971    7  HPFS/NTFS
/dev/sda7           10511       14462    31744408+   7  HPFS/NTFS
/dev/sda8           14463       18414    31744408+   7  HPFS/NTFS
/dev/sda9           18415       22366    31744408+   7  HPFS/NTFS
/dev/sda10          22367       26318    31744408+  83  Linux
/dev/sda11          26319       26580     2104483+  82  Linux swap / Solaris
/dev/sda12          26581       35751    73666026    7  HPFS/NTFS
/dev/sda13          35752       45419    77658178+   7  HPFS/NTFS
/dev/sda14          45420       48019    20884468+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x361f1336

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13      214271  1721028383+   7  HPFS/NTFS
/dev/sdb3          214272      243153   231993088   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde786b59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdd: 2048 MB, 2048728064 bytes
64 heads, 63 sectors/track, 992 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41c43198

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         992     1999749+   6  FAT16

Disk /dev/dm-0: 2000.0 GB, 1999999991808 bytes
255 heads, 63 sectors/track, 243152 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x361f1336

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2              13      214271  1721028383+   7  HPFS/NTFS
/dev/dm-0p3          214272      243153   231993088   83  Linux

Disk /dev/dm-2: 104 MB, 104857600 bytes
255 heads, 63 sectors/track, 12 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x2052474d

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?         410      119791   958924038+  70  DiskSecure Multi-Boot
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(365, 99, 47) logical=(409, 142, 41)
Partition 1 has different physical/logical endings:
     phys=(371, 114, 37) logical=(119790, 20, 38)
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-2p2   ?      121585      234786   909287957+  43  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 51) logical=(121584, 74, 6)
Partition 2 has different physical/logical endings:
     phys=(364, 116, 50) logical=(234785, 103, 28)
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-2p3   ?       14052       14052           5   72  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(288, 116, 47) logical=(14051, 94, 29)
Partition 3 has different physical/logical endings:
     phys=(372, 101, 51) logical=(14051, 94, 38)
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-2p4          164483      164486       25945    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(164482, 130, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(164485, 188, 41)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-3: 1762.3 GB, 1762333064704 bytes
255 heads, 63 sectors/track, 214258 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-3p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-3p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-3p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-3p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/dm-4: 237.6 GB, 237560922112 bytes
255 heads, 63 sectors/track, 28881 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x00000000

Disk /dev/dm-4 doesn't contain a valid partition table

```

---

