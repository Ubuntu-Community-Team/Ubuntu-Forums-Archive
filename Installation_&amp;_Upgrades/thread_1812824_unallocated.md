---
title: "unallocated?"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-07-26
what is unallocated partition for, it exists in Gparted, but does not in Win7 disk management?


[ATTACH]198557[/ATTACH]


[ATTACH]198558[/ATTACH]

---

### Post by Quackers on 2011-07-27
That's not unallocated, it's a NTFS partition that may need a chkdsk running on it.

---

### Post by plucky on 2011-07-27
> **Matrix01 said:**
> what is unallocated partition for, it exists in Gparted, but does not in Win7 disk management?


The un-allocated partition is 1Mbyte in size.

Don't bother about it as you can only move the start of a partition,and that would mean moving all your data in the partition as well,for 1 Mbyte it is just not worth it.

Good Luck

---

### Post by Mark Phelps on 2011-07-28
> **Matrix01 said:**
> what is unallocated partition for, it exists in Gparted, but does not in Win7 disk management?

That is a normal side-effect of partition alignment.  Sometimes, when partitions get created, they leave some space unallocated -- on both ends.

To change this, you would need to mess with your Win7 OS partition in Win7 Disk Management (NOT using GParted) -- and it's likely that Win7 won't let you resize to use that space.

I would just ignore it.

---

