---
title: "Any experience with ext4 recovery? Latest kernel update ran amok."
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by kelpdip on 2011-01-27
[IMG]http://lh4.ggpht.com/_Gdk6k_HJt8w/TUHmFfdpbCI/AAAAAAAACNE/xX19r7NXc1M/Screenshot-1.png[/IMG]

After the latest 10.04 automatic update ( including kernel 2.6.28(?) ) I can no longer boot past grub. I wasn't too worried and planned a fresh install until I found my /home partition was toast as well. It is partially backed up, but I would like to recover it. It was around 150 gigs of ext4.

---

### Post by coffeecat on 2011-01-27
Don't do anything just yet. The 'unallocated' in Gparted doesn't necessarily mean that your partitions are lost. If there is an irregularity in the partition table, Gparted will do this. Boot up from the live CD and post the terminal output of:

```
sudo fdisk -lu
```Then we can see what's what.

---

### Post by kelpdip on 2011-01-27
Thanks, but I used testdisk to rescue the handful of things I didn't want to lose. I think I will try a full reinstall anyway.

Considering it's a netbook, it has a basic Ubuntu install with very few packages and should be a breeze to reinstall from USB. The most difficult thing will be restoring the Evolution mail settings. No problem.

Also I'm wondering if the file system failure had nothing to do with the kernel update and may have been a symptom of more serious HD problems.

---

