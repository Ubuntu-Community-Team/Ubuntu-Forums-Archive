---
title: "newer kernels don't like me"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by iaw4 on 2010-08-22
This is actually on a server installed.

everything works fine with the original kernel, 2.6.32-21-server.  I have a root fs on /dev/sda1, and a user file system /home on a RAID-1 mdadm-instered /dev/sdb2 and /dev/sdc2.  the fstab refers to partitions by UUID.

ubuntu updates my kernel to 2.6.32-21-server (with config and initrd and abi and vmcoreinfo files [not sure what those are].  on reboot, it works for a long while, until it gets to tell me that the /dev/sdc1 is ok (no fsck needed), and then it just waits.  and waits.  and waits.  I can ctrl-alt-delete for a nice clean shutdown.  (rescue boot for 2.6.32-24 does not get beyond the looping stage, so it is not useful here.  ctrl-c did not interrupt and continue, either.)

this is all very confusing.  first of all, I made a clean filesystem on /dev/sdc1, and set its partition type to 14 (hidden FAT).  I did the same on /dev/sdb1.  I wonder why fsck even bothers with trying to check these two partitions.  as far as it is concerned, they should not be checked.

the older kernel, 2.6.32-21-server is perfectly happy.  It can boot into the same volume, reporting that it fsck checks /dev/sda1 and /dev/md1.  I can see this in boot.log .  (how do I keep the previous boot log??)

advice appreciated.

/iaw

---

