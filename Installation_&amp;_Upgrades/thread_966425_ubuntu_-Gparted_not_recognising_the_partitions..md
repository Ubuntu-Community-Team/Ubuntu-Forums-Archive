---
title: "ubuntu -Gparted not recognising the partitions."
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by parvathy on 2008-11-01
i have a dell m1530 laptop and want to have a dual boot -(xp and ubuntu).
I installed xp. while installing ubuntu gparted is showing the entire disk as an unallocated block. i tried testdisk. but it is showing all the partitions correctly... 
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  3823 254 63   61432497 [Windows XP]
 2 E extended              3824   0  1 21670 254 63  286712055
 3 P Linux Swap           20652   0  1 21670 254 63   16370235
 4 P HPFS - NTFS          21671   0  1 24857 254 63   51199155 [Windows Vista]
Space conflict between the following two partitions
 2 E extended              3824   0  1 21670 254 63  286712055
 3 P Linux Swap           20652   0  1 21670 254 63   16370235
   X extended              3824   0  2 20651 254 63  270341819
 5 L HPFS - NTFS           3824   2  1 20651 254 63  270341694 [Docs]





what should i do now???
can anybody please help me....

---

