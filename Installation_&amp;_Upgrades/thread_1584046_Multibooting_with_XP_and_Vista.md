---
title: "Multibooting with XP and Vista?"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by 2009Prius on 2010-09-28
I have a laptop that already duel boots to Vista and XP. Is it possible to add Ubuntu to a 10 GB unused space on the hard drive? 

Some more details: It came with Vista on one partition and factory backup on another. I added a partition for XP and another one for general storage. Now I have shrunk the Vista volume to make the 10 GB blank space. Vista refuses to make a new partition out of that. Ubuntu installer can't seem to use that blank space either. :confused:

---

### Post by Rubi1200 on 2010-09-28
You cannot use more than 4 primary partitions on most modern drives.

The best thing to do, in my opinion, is have 3 primary and 1 extended partition. 

Within the extended partition you can then create a logical partition to install Ubuntu.

Ubuntu will happily install into a 10GB logical partition.

Hope this helps.

---

### Post by 2009Prius on 2010-09-28
> **Rubi1200 said:**
> You cannot use more than 4 primary partitions on most modern drives.

The best thing to do, in my opinion, is have 3 primary and 1 extended partition. 

Within the extended partition you can then create a logical partition to install Ubuntu.

Ubuntu will happily install into a 10GB logical partition.

Hope this helps.

Thank you this makes sense! I didn't know Ubuntu can be installed into a logical partition. Thanks again! :)

---

### Post by Rubi1200 on 2010-09-28
I haven't tried all Linux distros, though I have played around with more than a few, but in my experience there is usually no problem installing Linux into a logical partition.

---

### Post by 2009Prius on 2010-09-29
Quick update. The installer (10.04) did not like the logical partition, but it was happy to take unallocated space and made its own partition. Thanks for all the help! :)

---

### Post by garvinrick4 on 2010-09-29
Logical partition must be in an extended partition (all the logical you want) it counts as a primary. As before me stated only 4 primary's to a HDD. Notice first 4 are primary and the rest are logical inside of sda3 which is the extended. Windows will only survive in a primary, Linux will survive anywhere. 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       15985   128192511    7  HPFS/NTFS
/dev/sda3           15985       36006   160819192+   5  Extended
/dev/sda4           36007       38913    23350477+   7  HPFS/NTFS
/dev/sda5           21349       22814    11775645   83  Linux
/dev/sda6           15986       17387    11261533+  83  Linux
/dev/sda7           17388       21348    31816701   83  Linux
/dev/sda8           22815       25394    20723818+   7  HPFS/NTFS
/dev/sda9           25395       26707    10546641   83  Linux
/dev/sda10          26708       29385    21511003+  83  Linux
/dev/sda11          29386       30683    10419200   83  Linux
/dev/sda12          30684       31992    10514511   83  Linux
/dev/sda13          31993       36006    32239616   83  Linux

---

### Post by Rubi1200 on 2010-09-29
> **2009Prius said:**
> Quick update. The installer (10.04) did not like the logical partition, but it was happy to take unallocated space and made its own partition. Thanks for all the help! :)
You are more than welcome :)

---

