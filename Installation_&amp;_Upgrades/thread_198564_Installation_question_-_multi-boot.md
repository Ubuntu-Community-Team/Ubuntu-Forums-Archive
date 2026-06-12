---
title: "Installation question - multi-boot"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by satimis on 2006-06-17
Hi folks,

I have a SATA HD of 80G in capacity with FedoraCore5_64 running on it.

# fdisk -l```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14        1734    13823932+  83  Linux
/dev/sda3            1735        3008    10233405   83  Linux
/dev/sda4            3009        9729    53986432+   5  Extended
/dev/sda5            3009        3262     2040223+  82  Linux swap / Solaris
```

/dev/sda1  /boot
/dev/sda2  /
/dev/sda3  /home
/dev/sda5  swap

occupying about 25G totally.  /dev/sda3 (/home) is 15G in size with a Data file running on it.

The ext partition has not been touched yet.  Now I want to create new partitions on the ext partitionins for installing Ubuntu 64bit on it as follows;

/dev/sda6  / (Ubuntu) 10G
/dev/sda7  /home  (Ubuntu)  5G


My questions are.

1) Can I repartition the ext partition manually before installing Ubuntu
2) On installing Ubuntu how to avoid the partitioning steps and installing / and /home direct to the partitions created for them in advance.
3) How to make /home of Ubuntu connected automatically at boot to the Data file on /home of FC5_64 without confusing its /home.
4) How to create multi-boot
5) Any advice to avoid corrupting the existing FC5_64

Please advise.  TIA

B.R.
satimis

---

