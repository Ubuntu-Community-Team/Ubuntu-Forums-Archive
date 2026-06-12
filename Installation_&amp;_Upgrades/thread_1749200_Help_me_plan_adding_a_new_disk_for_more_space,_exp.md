---
title: "Help me plan adding a new disk for more space, expanding Linux RAID, Lucid"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by sporto on 2011-05-04
Hi All,

I have 4 HDDs in my "NAS" system but would like to add a 5th to gain additional space. I want to really think about it in advance so that I have the best chance of success.

Each HDD looks like this:

200MB (/boot)
2GB(Swap)
1.48TB (LVM)

Boot partitions connected in mirrored mode.
Swap partitions connected in RAID 10 mode.
LVM partitions connected in RAID 5 mode.

The LVM has two LVs, one for the root file system and one for the "NAS".

grub-install was run on each HDD so that the system can always boot.

I'm running out of room so would like to buy a 5th HDD.

I was thinking that expanding my system would work as follows...

Backup a partition table (any as all are the same) using DD.

Install the new disk.

Write the backed up partition table to the new HDD.

Use the instructions here: [https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)
to add and grow each array.

Resize the root filesystem and nas partitions - does resize2fs support resize2fs?

What do I use if anything to resize /boot and /swap?

Anything I've forgotten?

Many thanks.

---

### Post by sporto on 2011-05-05
bump

---

