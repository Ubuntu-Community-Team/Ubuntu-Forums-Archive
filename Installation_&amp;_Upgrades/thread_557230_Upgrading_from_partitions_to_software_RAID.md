---
title: "Upgrading from partitions to software RAID"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by BobMUK on 2007-09-22
Hi
I've been running Ubuntu 6.06 for some time on my home server/PVR... I've just bought 4 250GB disks with the intention of moving over to software RAID 5 instead of the "normal" partitions it was running from.

So I've taken a full backup of my system, done a fresh install from CD to the 4 disks (configured as RAID 5) and I'm now booted into the fresh install running from the RAID array.

I'm about to start restoring my backup and I *think* all I need do is preserve a copy of the newly created /etc/fstab, untar my backup to /, and modify GRUB's parameters in menu.lst to reflect the new location of / (root=/dev/mapper/pvrvg-rootlv)

Have I missed anything?
Any help appreciated!!

Bob

---

