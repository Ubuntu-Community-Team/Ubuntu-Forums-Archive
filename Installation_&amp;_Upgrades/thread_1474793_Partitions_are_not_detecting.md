---
title: "Partitions are not detecting"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by gyaswanth on 2010-05-06
Hi,

I am trying to install Ubuntu 10.04 over old version 9.10.  Mine is Dell laptop with Vista and Ubuntu running as dual boot. While  installing Ubuntu 10.04, it is saying 'there are no Operating systems"  and no partitions were detected.

I tried to use  'partman/alignment=cylinder' while booting, but it couldn't help.

FYI,  My laptop has 4 primary partitions

Any help would be  appreciated!!

Thanks!

---

### Post by VMC on 2010-05-06
Output from this command, ```
sudo fidsk -l
```, Also did you use the Manual method from LiveCD?

---

### Post by gyaswanth on 2010-05-06
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30010       30401     3148708+   c  W95 FAT32 (LBA)
/dev/sda2               7        5228    41945715    7  HPFS/NTFS
/dev/sda3            5229       30401   202202122+   f  W95 Ext'd (LBA)
/dev/sda5           10328       16065    46080000    7  HPFS/NTFS
/dev/sda6           16065       21164    40960000    7  HPFS/NTFS
/dev/sda7           21164       30009    71048192    7  HPFS/NTFS
/dev/sda8           30010       30401     3148708+   0  Empty
/dev/sda9            5229        6444     9767457   83  Linux
/dev/sda10           6445        6809     2931831   82  Linux swap / Solaris
/dev/sda11           6810       10327    28258303+  83  Linux

Partition table entries are not in disk order

Yes, I did used CD for installing.

Thanks!

---

### Post by gyaswanth on 2010-05-08
No luck with the CD.
I have upgraded to 10.04 by using Network Upgrade. :)

Thanks!

---

