---
title: "How can I stop fsck from running after booting other partitions"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by vayu on 2013-04-26
Whenever I boot from one partition after having booted from a different one, there is a forced fsck.   I've tried setting fstab 6th column to 0.  That does not seem to affect the dirty mark the drive gets from being mounted by another OS.  It does stop from the every 30 boots check which I would rather keep (but am willing to forego if it means not having a disk check every time I boot from one OS to another).

How can I stop fsck from running after booting from another partition? (and hopefully keep a periodic fsck)

(all partitions are ext4, there is W7 but it's rarely booted, so not part of the problem)

---

### Post by vayu on 2013-04-27
I had the wrong symptoms. It's running fsck every boot. I'm pretty sure my problem is this bug: [bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1073433")  For those searching, it's a long confusing thread. Here's my possibly innacurately paraphrased take,  apparently there is some timing issue in the order of processes being shutdown and the fs is not being properly unmounted.  People had different workarounds that weren't really part of the problem but would alter the timing of the shutdown process.  I chose to uninstall network manager and install wicd in its place. That worked for me (temporarily I suppose until I update or install something that alters the order or timing of the shutdown process).

---

