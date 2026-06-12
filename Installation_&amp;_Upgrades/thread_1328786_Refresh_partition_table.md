---
title: "Refresh partition table"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by LeeM on 2009-11-16
Something is hosed up in my partition table apparently. Gparted and the Karmic Live CD both say there are no partitions on my disk (sda). However there really are - here is the response to sudo fdisk -l:
[INDENT]sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           19132       19457     2618563+   c  W95 FAT32 (LBA)
/dev/sda2   *           1        7809    62725761    7  HPFS/NTFS
/dev/sda3           10742       19457    70011270    f  W95 Ext'd (LBA)
/dev/sda4            7810       10741    23551290   83  Linux
/dev/sda5           19132       19457     2618563+  dd  Unknown
/dev/sda6           18769       19131     2915734+  82  Linux swap / Solaris
/dev/sda7           14944       18442    28105654+  83  Linux
/dev/sda8           10742       14764    32314684+  83  Linux
/dev/sda9           14765       14943     1437786   82  Linux swap / Solaris

Partition table entries are not in disk order[/INDENT]

Another thread suggested refreshing the partition table, using
sudo blockdev --rereadpt /dev/sda

But everytime I try to issue this command, I get 
BLKRRPART: Device or resource is busy
even though I have just started up the Live CD (or Knoppix). How can I refresh the partition table - or should I be doing something else??

---

