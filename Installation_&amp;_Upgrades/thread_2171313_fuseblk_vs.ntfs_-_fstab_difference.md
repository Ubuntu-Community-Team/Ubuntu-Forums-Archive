---
title: "fuseblk vs.ntfs - fstab difference"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by BarryD9545 on 2013-08-30
Hey all-

While setting up my external NTFS HD to automount, I ran

* $  mount|grep ^'/dev'*

and got 

* /dev/sdb1 on /media/barry type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)*

for my drive info.

I know that fuseblk is how ntfs drives are displayed here.  I was curious if fuseblk could be interchanged with ntfs in the fstab file as well.
in other words are

* /dev/sdb1 /media/barry    _ntfs-3g_    defaults  0     0*
and
* /dev/sdb1    /media/barry    _fuseblk_    defaults  0     0*

Interchangeable?

Curiosity and all.

---

