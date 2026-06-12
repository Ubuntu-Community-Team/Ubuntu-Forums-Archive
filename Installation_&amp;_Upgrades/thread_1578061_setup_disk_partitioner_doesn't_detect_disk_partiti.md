---
title: "setup disk partitioner doesn't detect disk partition table"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by cooprocks123e on 2010-09-19
Hello. I have quite an interesting issue. The disk partitioner built into the installer does not detect the partition table of my SATA disk, so it shows the disk and then when I select it, it asks to make a new partition table. There is a normal partition table and my computer boots vista. However, when I use fdisk from the installer, it shows all the partitions. I am looking for a way to use fdisk with the installer or to use a script to install ubuntu _easily_.

Thanks in advance,
        Cooper

---

### Post by garvinrick4 on 2010-09-19
What partitioner are you using?

---

### Post by srs5694 on 2010-09-19
First, check [this Web page I wrote,](http://www.rodsbooks.com/missing-parts/index.html) which describes one possible cause of the symptoms you report. I can't guarantee that your problem has the same root cause, but chances are fairly high that it's at least similar.

Second, if you need more help, please post the output of "sudo fdisk -lu", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That will help us diagnose and fix the problem.

---

### Post by cooprocks123e on 2010-09-20
Yeah, that was it. Thanks for diagnosing. Output:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc53f7d3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20338289    10169113+   7  HPFS/NTFS
/dev/sda2   *    20338688   481183743   230422528    7  HPFS/NTFS
/dev/sda3       481183744   501661695    10238976    7  HPFS/NTFS
/dev/sda4       501661696   625151999    61745152    f  W95 Ext'd (LBA)
/dev/sda5       501663744   583583743    40960000    7  HPFS/NTFS

Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7905278     3952623+   7  HPFS/NTFS

```

Anyways, I fixed it by deleting that partition with fdisk, and now Ubuntu is installing.

Thanks,
Cooper

---

