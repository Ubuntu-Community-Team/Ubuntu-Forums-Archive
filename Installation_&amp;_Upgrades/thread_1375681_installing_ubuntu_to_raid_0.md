---
title: "installing ubuntu to raid 0"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Keddy on 2010-01-08
Hi there, 

I've 2 x 250gb harddisks as software raid 0. While i was installing windows, i created 2 partitions..now 1 partition has windows, the other 220gb partiton is all empty.

My question is, is it possible to install Ubuntu 9.10 x64 to this partition without messing up my system?

If it's possible, how am i going to configure my boot setup?

---

### Post by dstew on 2010-01-08
I think the [Alternate Install CD]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") can install to a software RAID. The only experience I have is creating a RAID5, and installing to it, from an earlier version of Ubuntu. I used a partition on the RAID5 for the Ubuntu root partition (mount point '/'). I booted using grub legacy (version 0.97). I created a small RAID1 array to hold my /boot partition because that version of grub could not recognize striped RAID, like RAID0 or RAID5. In fact, it could not recognize mirrored RAID either, but since both parts of the RAID1 were identical, it just booted off of one part without knowing the mirrored part was even there! It probably would have been more honest to just use a small unRAIDed /boot partition. Anyway, once the Linux kernel was booted from the /boot partition, the kernel recognized the RAID5 array and all went smoothly.

I do not think the new grub2 can boot from striped RAID either. [Here is a thread discussing this]("http://ubuntuforums.org/showthread.php?t=1352656&page=2").

Also, I am not sure the Alternate Install CD will recognize a software RAID designed to run under Windows. Maybe it will. You might start the install process, and see if it does.

---

