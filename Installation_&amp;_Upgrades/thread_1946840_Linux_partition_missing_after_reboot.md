---
title: "Linux partition missing after reboot"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by jhume on 2012-03-25
Hi!

I installed Ubuntu 10.04 using Wubi with Windows XP previously installed. While running, Ubuntu hanged and I had to restart. But now Ubuntu won't boot and I receive the following error:

> mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target file system doesn't have /sbin/init
No init found. Try passing init= bootarg

Then I booted with Live CD and using fdisk found that my Linux partition is no longer available. This is what I got:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03c103c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7776    62460688+   7  HPFS/NTFS
/dev/sda2            7777       19456    93819600    f  W95 Ext'd (LBA)
/dev/sda5            7777       11728    31744408+   7  HPFS/NTFS
/dev/sda6           11729       15552    30716248+   7  HPFS/NTFS
/dev/sda7           15553       19456    31358848+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42c16954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9642    77441024    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            9642       13594    31743755    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sdb3           13594       19457    47102549+   f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sdb5           13594       19457    47102548+   7  HPFS/NTFS


I tried to install TestDisk but could not do that either. 

What should I do to recover my partition?

Thanks!

---

### Post by darkod on 2012-03-25
No linux partition is missing. Wubi installs virtual ubuntu inside windows on the existing ntfs partitions. It never creates any linux partitions.

As far as why wubi broke down, I have no idea, I don't use it.

Also any repair done on wubi will not be the same as with proper dual boot ubuntu so be careful about tutorials and instructions. Most are for the proper ubuntu.

If you want to keep using wubi you are welcome, but I strongly suggest you consider creating a dual boot. Wubi is not meant to be a long term install, just a quick try. Usually it can break during updates or upgrades, on top of that repairing it is not as simple as the stand alone ubuntu because it is inside windows.

---

### Post by jhume on 2012-03-25
> **darkod said:**
> No linux partition is missing. Wubi installs virtual ubuntu inside windows on the existing ntfs partitions. It never creates any linux partitions.

As far as why wubi broke down, I have no idea, I don't use it.

Also any repair done on wubi will not be the same as with proper dual boot ubuntu so be careful about tutorials and instructions. Most are for the proper ubuntu.

If you want to keep using wubi you are welcome, but I strongly suggest you consider creating a dual boot. Wubi is not meant to be a long term install, just a quick try. Usually it can break during updates or upgrades, on top of that repairing it is not as simple as the stand alone ubuntu because it is inside windows.

Thanks for the suggestions, I always thought so, but Ubuntu does not mentions sufficient warnings with Wubi on their site.

But now is there a way to recover from this situation?

---

### Post by darkod on 2012-03-25
Depending on the letter of the partition you selected as destination during the install, there should be folder ubuntu in it. The main virtual root disk is inside in /ubuntu/disks/root.disk

Look here for example how you mount that disk from live mode:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

Doing the fsck suggested there might also help check the root.disk for corruption. Just do the fsck before doing the mount -o loop command because you need to run fsck on unmounted partitions.

And then after you mount it you should be able to look inside as suggested there.

Other than that, no idea at the moment. It depends what happened with it.

---

### Post by jhume on 2012-03-25
> **darkod said:**
> Depending on the letter of the partition you selected as destination during the install, there should be folder ubuntu in it. The main virtual root disk is inside in /ubuntu/disks/root.disk

Look here for example how you mount that disk from live mode:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

Doing the fsck suggested there might also help check the root.disk for corruption. Just do the fsck before doing the mount -o loop command because you need to run fsck on unmounted partitions.

And then after you mount it you should be able to look inside as suggested there.

Other than that, no idea at the moment. It depends what happened with it.

Many thanks, I will try your suggestion.

---

### Post by jhume on 2012-03-26
> **darkod said:**
> Depending on the letter of the partition you selected as destination during the install, there should be folder ubuntu in it. The main virtual root disk is inside in /ubuntu/disks/root.disk

Look here for example how you mount that disk from live mode:
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)

Doing the fsck suggested there might also help check the root.disk for corruption. Just do the fsck before doing the mount -o loop command because you need to run fsck on unmounted partitions.

And then after you mount it you should be able to look inside as suggested there.

Other than that, no idea at the moment. It depends what happened with it.

The suggestions on the page link you gave worked perfectly well. I am back on Ubuntu. Thanks again!

And I would like to mention to anyone trying to find out their /dev/sd__ can do so from System > Administration > Disk Utility.

---

### Post by darkod on 2012-03-26
Glad you got it sorted.

You can mark the thread as Solved in Thread Tools above the first post.

---

