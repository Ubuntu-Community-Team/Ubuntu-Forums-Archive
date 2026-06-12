---
title: "Partition data recover"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by seti@tquadrado.com on 2005-05-14
Hi,

i had a partition on my Ubuntu 4.10 laptop that i wanted to keep when installing Ubuntu 5.04.
When making partitions on 5.04 installation, i created a newer one, copied the data from the original Fat32 partition, and it told me to make the new partition a Fat partition too. Ok. I did it. I installed 5.04 and the data was there on the new partition.

I needed to reinstall 5.04, and did nothing in the partition containing my data. When everything was done, i never again saw the data partition. This must have beem because i did not created a mount poit for that partition.

The problem is that i made a "mkfs /dev/hda2" and my question is: did this destroy all the data on the partition ? It was not even mounted.

I went back to the partition manager and created a mount point to "/data", not formatting, and now it appears empty.

glup, i have important emails there...
I dont sleep for 2 days...
help please...

---

### Post by alastair on 2005-05-14
If you made a new filesystem on the partition then the data is gone - unless you wish to pay for data recovery, or find an expert to recover it (the data is still there perhaps).

The "mkfs" command works on a partition (e.g. hda1) and is equivalent to "format" in DOS/XP.

---

### Post by nad on 2005-05-14
If that data partition was /dev/hda2, you certainly did make a newly formatted file system there of type ext2 (unless ext3 is now the default).

In order to make a new file system, the device needs to be necessarily unmounted.

The ubuntu installer needs a little work as more people are installing in somewhat complicated configurations and the default install makes some poor and/or non-prominent/unclear assumptions. Perhaps a more prominent message to review partitioning choices, instructions, examples and a bootloader howto with additional choices and examples.

---

