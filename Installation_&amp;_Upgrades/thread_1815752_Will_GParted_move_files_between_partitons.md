---
title: "Will GParted move files between partitons"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by 7cardcha on 2011-07-31
If I shrink the main partition which Oracle Linux is on and make a new partition will GParted automatically move the files of part you want to unallocate and put it on the free part of the Oracle Linux partition.

---

### Post by 73ckn797 on 2011-07-31
It should not be a problem. I have shrunk partitions before and it did not lose anything from the partition except the extra space.

---

### Post by Markmental on 2011-07-31
all shrinking a partion does is take of a chunk of unused space. So you should be fine.

---

### Post by varunendra on 2011-08-01
> **7cardcha said:**
> If I shrink the main partition which Oracle Linux is on and make a new partition will GParted automatically move the files of part you want to unallocate and put it on the free part of the Oracle Linux partition.
The files will automatically be moved to allow creation of the empty space. But it is always recommended to backup your important files before performing partition manipulation tasks, as there is always some potential risk involved.

Besides, it sometimes takes too much time to move files automatically during a partition resize operation (many times more compared to a normal copy/move). Therefore I prefer to move as many files as possible to another partition (which is not to be touched) and then perform the resize operations.

---

### Post by Elfy on 2011-08-01
Files won't be moved between partitions. They'll get moved if you resize one - but only within the partition.

---

