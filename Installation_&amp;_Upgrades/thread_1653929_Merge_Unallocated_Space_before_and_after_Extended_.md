---
title: "Merge Unallocated Space before and after Extended partition"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by eshu68 on 2010-12-27
Hi,

I want to merge the Unallocated Space before and after the extended partition which is used by Ubuntu.

PS : I tried GParted from Live CD as well as from my system, but I cannot merge the partitions.

Thanks

---

### Post by dabl on 2010-12-27
In your graphic, the extended partition is mounted.  You can't change the configuration of a mounted partition.

I would advise booting a Live CD that has GParted on it.  Parted Magic Live CD would be a good choice.

Then, with no partitions mounted, delete the first partition, and also the "last", meaning the bottom one in your graphic which is identified as /dev/sda1.  When you delete them, the space becomes "unallocated" as viewed with GParted.  So then you can merely expand the extended partition in both directions, to absorb the unallocated space.

NOTE/CAUTION:  When you delete a "leading" partition, the following partitions will be renumbered.  So, /dev/sda2 might become /dev/sda1, etc.  This has implications for Grub and /etc/fstab.  You need to know how to handle the necessary changes to those parts of your system, or else you might find yourself looking at a failed Grub boot prompt.

---

