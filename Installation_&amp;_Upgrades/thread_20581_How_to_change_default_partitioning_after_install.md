---
title: "How to change default partitioning after install?"
date: 2005-03-17
forum: Installation &amp; Upgrades
---

### Post by gratefulfrog on 2005-03-17
I have been running 64bit Hoary, installed using default partitioning of my single 160GB SATA drive.

Now I would like to repartition my disk so that I can install a 32bit Hoary.

Can anyone suggest what partitions must be changed, and to what values so that I can reduce the size of the Hoary use to around 50GB, leaving the rest for the other OS.

Ideally, I would like to know the suggested parted commands to do the resizing and creation of any required partitions for a HOARY 32bit.

Any help would be welcome!

Here are my current partitioning info as from parted:

```
Disk geometry for /dev/sda: 0.000-152627.835 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031 149699.443  primary   ext3        boot
2     149699.443 152625.344  extended
5     149699.474 152625.344  logical   linux-swap

Disk geometry for /dev/sda1: 0.000-149699.412 megabytes
Disk label type: loop
Minor    Start       End     Filesystem  Flags
1          0.000 149699.412  ext3

Using /dev/sda2
(parted) print
Error: Can't have a partition outside the disk!

Using /dev/sda5
(parted) print
Disk geometry for /dev/sda5: 0.000-2925.870 megabytes
Disk label type: loop
Minor    Start       End     Filesystem  Flags
1          0.000   2925.870  linux-swap
```

---

