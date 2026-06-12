---
title: "Windows 7 and Ubuntu 10.10 dual-boot - can not create a new partition"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Simple Nok on 2011-03-14
I've shrunk my Windows partition to ~200GB and made ~100GB of free space for Ubuntu BUT .. it doesn't allow me to create a new partition there as I already have 4 primary ones.

Since all of the given partitions ( including Recovery and Tools ) can not be touched ( removed ), I have no idea on how to solve this ..

Anyone ?

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed2ae46e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       24153   193799168    7  HPFS/NTFS
/dev/sda3           36901       38901    16060416    7  HPFS/NTFS
/dev/sda4           38901       38914      105816    c  W95 FAT32 (LBA)

Disk /dev/sdb: 1017 MB, 1017117696 bytes
255 heads, 63 sectors/track, 123 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0268fba1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         124      993247+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(122, 254, 63) logical=(123, 167, 42)
```

---

### Post by oldfred on 2011-03-14
You do have to backup & delete one partition, so you can then create an extended partition to hold the logicals that Ubuntu needs.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

---

