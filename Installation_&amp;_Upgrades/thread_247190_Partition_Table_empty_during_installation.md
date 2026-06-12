---
title: "Partition Table empty during installation"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by FIONEX on 2006-08-30
I partitioned my drive in windows using Acronis Disk Editor.  I have the following partition table:

PQService 3Gb Primary FAT32 Hidden
Linux 9.5Gb Logical Ext3
Swap 560Mb Logical SWAP
Windows (C:) 15 Gb Primary FAT32
Storage (D:) 27.6 Gb Logical FAT32

When I boot into windows, the partition table is visible and all is well.  When I try to install ubuntu linux 6.06 and choose to manually edit the partition table, then I get an empty partition table.  All the space is unallocated.  Any ideas?

---

### Post by FIONEX on 2006-08-30
For the record, it was because I had too many primary partitions.  I switched the linux partition and swap to Logical partitions and everything was fine.  Linux was counting the SWAP partition as a primary.  The Acronis program didn't count it as a primary.

---

