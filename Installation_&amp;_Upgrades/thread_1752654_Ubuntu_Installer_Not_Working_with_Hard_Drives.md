---
title: "Ubuntu Installer Not Working with Hard Drives"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by simpleeddie on 2011-05-08
Hi All.

I have tried to install Ubuntu 11.04 onto my machine (will be a dual-boot, I have Windows on one hard drive and will be installing ubuntu to the second hard-drive).

When I go to pick the hard drive to install Ubuntu to, I only get one option - /dev/mapper/nvidia_bafdfceb1 (500GB)

This shouldnt be happening - I have RAID turned off in the BIOS, and my two hard drive are 230 and 320 Gbs (230 with windows, 320 where i want to install Ubuntu).

here is my fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00034fe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29164   234259798+   7  HPFS/NTFS
/dev/sda2           29165       30402     9936897    5  Extended
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000950a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/dm-1: 500.1 GB, 500118585344 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x000950a8

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/dm-2: 320.1 GB, 320070483968 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-2p1   ?      120528      234814   918008208   4f  QNX4.x 3rd part
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/dm-2p2   ?      119381      153271   272218546+  73  Unknown
Partition 2 does not end on cylinder boundary.
Partition 2 does not start on physical sector boundary.
/dev/dm-2p3   ?      113202      147075   272087568   2b  Unknown
Partition 3 does not end on cylinder boundary.
Partition 3 does not start on physical sector boundary.
/dev/dm-2p4   ?      177064      177067       27487   61  SpeedStor
Partition 4 does not end on cylinder boundary.
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 4040 MB, 4040724480 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         492     3945920    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 64, 21)
```

Please let me know what I could do to rectify this so that I can get ubuntu installed on my second harddrive!

Cheers

---

### Post by ronparent on 2011-05-08
As you have discovered, turning off raid in bios is inadequate. The raid meta data written to the drives is persistent and is still detected when the raid is no longer in use. You need to use dmraid to erase that meta data.

To do this open a terminal and enter 
> sudo dmraid -rE /dev/sda
for each drive (sda, sdb etc) previously used as part of a raid set.

Let us know how you make out.

---

