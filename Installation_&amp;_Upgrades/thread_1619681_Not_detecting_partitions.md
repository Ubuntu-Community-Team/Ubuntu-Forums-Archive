---
title: "Not detecting partitions"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by Shishant on 2010-11-12
Hello,

I bought the new harddisk so was doing a fresh install of ubuntu (Already installed win7)

But ubuntu setup is not detecting the partitions correctly it is showing 4 partitions but I have 5 (and +1 which is created by win7 of 100mb for system usage)

Setup is showing total 4 partitions and clubing all the partitions together and showing as 785gb and one partition is not detected at all and the other 3 partitions only one is correct 100mb win7 system usage partition.


I have 4 partitions ntfs and 1 partitions exFat, I had created exFat hoping ubuntu setup will detect it as different partition but that is not shown in partitions selection menu.

---

### Post by sikander3786 on 2010-11-12
Hi.

From terminal under Applications > Accessories, please post the output of

```
sudo fdisk -l
```

---

### Post by Shishant on 2010-11-12
This is screenshot of win7 [http://i52.tinypic.com/v83nyp.png](http://i52.tinypic.com/v83nyp.png)

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8177cf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        1014+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13       26122   209715200   42  SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           26122      121602   766942936   42  SFS
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 4043 MB, 4043284480 bytes
125 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000ac20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1018     3944719    c  W95 FAT32 (LBA)


---

### Post by sikander3786 on 2010-11-12
Well you have dynamic discs in Windows. I guess you'll need to convert them to basic partitions to recognize them in Ubuntu. I don't think Ubuntu will be able to recognize them properly otherwise...

Wait for some other suggestions.

---

### Post by Shishant on 2010-11-12
Anybody else can help?

---

### Post by srs5694 on 2010-11-12
I concur with sikander3786. I'll add that the [Partition Wizard](http://www.partitionwizard.com/) software is supposed to be able to convert from Windows dynamic disks to standard partitions without data loss; however, I've never used this software and so I can't verify this claim. As a general rule, you should always back up your important data before making low-level partitioning changes, so please do so before you attempt such a change.

---

### Post by cybergnome on 2010-11-12
Read the man pages on FDISK and the following: [http://tinyurl.com/2cw327j](http://tinyurl.com/2cw327j).  See if this helps clear things up.

---

