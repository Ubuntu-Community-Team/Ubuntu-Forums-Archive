---
title: "How to select root partition"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by FrankRad on 2007-03-15
I have partitioned my harddisk, installed Windows and now I have two partitions left, one ext3 partition of 4GB, and 1 swap partition of 1 GB. When I try to install Ubuntu on them, I select only those two in the partition select window, select '\' for the ext3 one and 'swap' for the swap partition.

At that point I get an error that no root partition is selected, and I'm unable to continue with the installation.

Help!

---

### Post by FrankRad on 2007-03-15
Ok, I fixed it by removing both, and making a new ext3 partition 4.5 GB in size.

So, it seems that the installer simply refuses to install to a disk that is only 4GB in size, without telling you so.

---

### Post by kidders on 2007-03-15
Hi there,

The path to the root partition is '/', not '\'.

---

