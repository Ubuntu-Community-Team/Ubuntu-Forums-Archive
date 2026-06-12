---
title: "Dual booting from 1 hard-disk"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by wburden on 2007-06-18
I have organized a 200 GB harddisk on the primary channel as follows:

120 GB allocated on /dev/hda1 as windows NTFS partition; 80 GB unallocated on /dev/hda2. 

I want to install Feisty Fawn (7,04) on the unallocated partition using GParted with Mount Points as follows - 10 GB for Root /, 2 GB swap, and the balance for /home.

I am confused by partition types and partition file systems - what is primary and what is extended. Also, when do I set the bootable flag for /?

---

### Post by confused57 on 2007-06-18
> **wburden said:**
> I have organized a 200 GB harddisk on the primary channel as follows:

120 GB allocated on /dev/hda1 as windows NTFS partition; 80 GB unallocated on /dev/hda2. 

I want to install Feisty Fawn (7,04) on the unallocated partition using GParted with Mount Points as follows - 10 GB for Root /, 2 GB swap, and the balance for /home.

I am confused by partition types and partition file systems - what is primary and what is extended. Also, when do I set the bootable flag for /?

See the "Plan Partitions" and "Desktop Install..." sections in this guide:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

You can have only 4 primary partitions on a hard drive, one of the primary partitions can be an extended partition, which can contain many logical partitions...Linux has no problem using logical partitions.

Basically, you'll select "Manual Partitioning"...click on the unallocated space, create new partition...then move the slider to 10 Gb for your root partition...select primary partition, mountpoint /, format ext3.
Do the same for swap...size it to 2 Gb, mountpoint swap, select logical partition...For home, use the rest of the unallocated space, mountpoint /home, format ext3, select logical partition.
Make sure not to select format for your Window's partition & you should be fine.

If you already have 3 primary partitions, which it appears you don't, you could select logical partition for all your Ubuntu mountpoints.

---

