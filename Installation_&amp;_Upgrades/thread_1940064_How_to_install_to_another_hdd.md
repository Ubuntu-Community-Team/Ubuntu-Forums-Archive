---
title: "How to install to another hdd?"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by jekylhyde on 2012-03-12
Hi
what can i do if i ran out of space in the installtion drive on which i installed ubuntu... but i want to install things... could i install it to a 2nd drive?

---

### Post by oldfred on 2012-03-13
How much space did you allocate?

You cannot easily install parts once installed, but you can create different partitions and install parts to those partitions. Many install /home to a different partition. And there are instructions for moving /home to another partition if you want those.

I normally suggest that all of the system be on one drive and let data be on which ever drive has space. I keep /home inside my / (root) but link all data from /mnt/data or /mnt/shared (NTFS) partitions that often are on another drive. Then I only use 20 or 25GB for every root install.

Post this:

sudo fdisk -lu
and
Mounted Partition sizes
df -Th | sort

---

