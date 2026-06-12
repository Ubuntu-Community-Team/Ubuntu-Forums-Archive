---
title: "boot disk becomes a raid member"
date: 2019-05-09
forum: Installation &amp; Upgrades
---

### Post by lvm on 2019-05-09
Installing 18.04 from scratch with GUI installer and default options on an empty disk, first reboot after the installation goes fine, second reboot fails into ramfs shell with 'gave up waiting for root filesystem device' with some UUID. blkid does NOT list partition with this UUID or any other partition from the boot disk but shows this disk without partitions (i.e. /dev/sda) with TYPE=linux_raid_member. This disk indeed was previously used in md raid. I tried zeroing some sectors at the start of the disk (dd if=/dev/zero of=/dev/sda bs=4096 count=65536) and reinstalling but it didn't help. What is going on and how can I use this disk?

---

### Post by TheFu on 2019-05-12
I'm replying only because nobody else has.

There are specific tools to remove the RAID markers from disks. I think the tools are different for the different sorts of RAID.  
Google found this: [https://ubuntuforums.org/showthread.php?t=1722440](https://ubuntuforums.org/showthread.php?t=1722440)

---

