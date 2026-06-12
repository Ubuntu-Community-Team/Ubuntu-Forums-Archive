---
title: "Ubuntu installation doesn't detect windows 7 installation and  hard drive partitions"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by mjnaderi on 2011-12-30
Hello

I had installed ubuntu 11.10 alongside windows 7 before. But for some reasons, I decided to remove both and install them again. After removing both operating systems, I installed windows 7.Now I want to install ubuntu 11.10 alongside windows. But It doesn't detect my windows 7 installation and it doesn't detect my hard drive partitions. Even it shows an error while trying to install inside windows.

Now I'm running ubuntu using "Try Ubuntu". It shows only one disk partition with unknown size.
When I open gparted, It shows whole my hard disk as one unallocated disk drive.

I tested following commands in terminal:
```

sudo sfdisk -luS && sudo fdisk -l

```And this is the result:
```

Disk /dev/sda: 77825 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63 285555374  285555312   7  HPFS/NTFS/exFAT
/dev/sda2     207493118 1250258624 1042765507   f  W95 Ext'd (LBA)
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     285555438 495267884  209712447   7  HPFS/NTFS/exFAT
/dev/sda6     495267948 579159314   83891367   7  HPFS/NTFS/exFAT
/dev/sda7     579159378 830817539  251658162   7  HPFS/NTFS/exFAT
/dev/sda8     830817603 1250258624  419441022   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1020 cylinders, 239 heads, 62 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1   *        62  15114359   15114298   b  W95 FAT32
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7f53b447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   285555374   142777656    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       207493118  1250258624   521382753+   f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda5       285555438   495267884   104856223+   7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       495267948   579159314    41945683+   7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sda7       579159378   830817539   125829081    7  HPFS/NTFS/exFAT
Partition 7 does not start on physical sector boundary.
/dev/sda8       830817603  1250258624   209720511    7  HPFS/NTFS/exFAT
Partition 8 does not start on physical sector boundary.

Disk /dev/sdb: 7743 MB, 7743995904 bytes
239 heads, 62 sectors/track, 1020 cylinders, total 15124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00068368

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62    15114359     7557149    b  W95 FAT32

```I am beginner to ubuntu and I don't know exactly what to do.
Please help me overcome the problem.

---

### Post by darkod on 2011-12-30
Gparted shows the disk as unallocated usually when there is a problem or corruption in the partition table.
You can take a look at fixparts which can scan the disk and do small repairs if necessary. It always better to backup your data first.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by coffeecat on 2011-12-30
> **darkod said:**
> Gparted shows the disk as unallocated usually when there is a problem or corruption in the partition table.
You can take a look at fixparts which can scan the disk and do small repairs if necessary. It always better to backup your data first.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

+1 to what darkod says. Fixparts should fix this for you. For the record, the partition table irregularity is here:

> **mjnaderi said:**
> ```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x7f53b447

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   [COLOR="Red"]285555374[/COLOR]   142777656    7  HPFS/NTFS/exFAT
Partition 1 does not start on physical sector boundary.
/dev/sda2       [COLOR="Red"]207493118[/COLOR]  1250258624   521382753+   f  W95 Ext'd (LBA)
Partition 2 does not start on physical sector boundary.
/dev/sda5       285555438   495267884   104856223+   7  HPFS/NTFS/exFAT
Partition 5 does not start on physical sector boundary.
/dev/sda6       495267948   579159314    41945683+   7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sda7       579159378   830817539   125829081    7  HPFS/NTFS/exFAT
Partition 7 does not start on physical sector boundary.
/dev/sda8       830817603  1250258624   209720511    7  HPFS/NTFS/exFAT
Partition 8 does not start on physical sector boundary.

```

The start of the extended partition, sda2, overlaps the end of the primary sda1 partition. It's the start sector of the sda2 partition which is wrong. Fortunately the start sector of the first logical partition, sda5, is OK. Fixparts should do the job for you.

---

### Post by mjnaderi on 2011-12-30
Thanks darkod and coffeecat for your help.

I read your advice a moment ago, but I solved the problem before it and before trying your solution.
I chose the last available solution, and here it is:
After several attempts, finally I decided to backup my data and format entire my disk and set up a new partition table using windows 7 installation. I did so and it worked.

I wasn't so lucky to try Fixparts.

Thank you again.

---

