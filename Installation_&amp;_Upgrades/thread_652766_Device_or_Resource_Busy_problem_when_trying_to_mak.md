---
title: "Device or Resource Busy problem when trying to make XFS filesystem"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by Fed on 2007-12-29
Hi folks.

I'm trying to make an XFS filesystem on a large partition (5TB). The background info is that its a RAID5 on a hardware controller, and that I used parted to make the partition but not the filesystem since the mkfs function in parted doesn't support XFS. The array is /dev/sda, sda0 is the swap, sda1 is a small ext3 partition with the OS itself, and /dev/sda2 is the large chunk of space. When I do:
mkfs.xfs /dev/sda2
All I get is:
mkfs.xfs: cannot open /dev/sda2: Device or resource busy
Any idea why? sda2 is not mounted anywhere, however sda1 (obviously) is. Is it not allowing me to make a filesystem on a different partition purely because sda1 is on the same device and is busy (since it's running the whole OS)? Is there no way I can override its complaining? Or figure out why it's busy if that really is the case?

Thanks a lot.

---

### Post by Fed on 2007-12-29
I figured it out eventually, case closed.

---

