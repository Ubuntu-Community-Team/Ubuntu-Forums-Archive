---
title: "RAID5 with xfs, missing 14% of available space?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by yatzr on 2008-07-15
I recently set up a test RAID5 using mdadm and 3x300GB (279GiB) drives.  These drives are completely separate from the main drive that has Ubuntu 8.04 on it.  I formatted using mkfs.xfs with default options and ended up with an array of only about 480GiB.  I'm assuming the size should be much much closer to 2 x 279 = 558GiB.  Did I do something wrong?  Does xfs reserve that much space for something else?  The journal can't take up that much space can it?  This is my first time using xfs, so I'm really unfamiliar with it.  Any help is greatly appreciated.

---

### Post by yatzr on 2008-07-15
nevermind, I found that I accidentally messed up when I was partitioning one of the drives.  I entered the wrong last cylinder on one drive making the partition only about 240GB.  All is good now.

---

