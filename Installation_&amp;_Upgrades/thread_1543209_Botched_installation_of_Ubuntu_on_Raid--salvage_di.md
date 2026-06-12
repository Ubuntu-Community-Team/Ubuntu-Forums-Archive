---
title: "Botched installation of Ubuntu on Raid--salvage disk?"
date: 2010-07-31
forum: Installation &amp; Upgrades
---

### Post by lhnitz on 2010-07-31
A couple of months ago I had a working raid-1 for data storage.  For some reason, my Ubuntu installation became corrupted and I tried reinstalaltion.   Between bad CDs, and cranky operating system, I managed to overwrite one half of the raid-1 data set.  Now I have an ordinary ext4 file system on one disk, and a disk partitioned for raid on the other disk.  That disk still has valid data on it.  

When I go to a mounting utility, I cannot list this drive to mount.  Is it possible to mount it without renaming the disk to ext4?  Should I be able to mount it (specifically mount both drives) simply be setting up explicit mount statements in fstab?  (I would be mounting the damaged raid1 disk and the undamaged raid1 disk under different names).

Thanks--some clear thought will be really helpful here!

---

