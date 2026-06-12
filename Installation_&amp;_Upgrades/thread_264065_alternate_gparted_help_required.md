---
title: "alternate gparted help required"
date: 2006-09-24
forum: Installation &amp; Upgrades
---

### Post by carverj on 2006-09-24
G'day,
      Am having problems with the partitioning step of a dual boot
install. I have a Pressario AMD 533 with ntfs on the first partition. First it crashed and now when I try to add a primary ext3 in the unallocated space, it comes up with a little yellow "!"
warning and doesn't recognise the partition (black border).it will not let me allocate a / partition in the final step and just has
the media mount point for the ntfs partition.
It also fails to recognise my secondary drive 
Could this be a bug with the alternate parted disk or is it likely that I have made the error?
Cheers guys

---

### Post by cotcot on 2006-09-24
You are not the only with this problem. Use the GParted LiveCD instead of the Dapper install CD for partitioning. You won't get the yellow "!" with this. Afterwards install Dapper of the partitions available.

---

