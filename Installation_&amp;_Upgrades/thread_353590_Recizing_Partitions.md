---
title: "Recizing Partitions"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by TBOL3 on 2007-02-04
I was trying to install 6.10, but in doing this, I cut my current Linux partition in half, now I have two empty halves, that I want together.  It there any way of combining these two halves without removing my windows side?

Current partition:
Small part for windows
Empty Partition 1 of 2
Empty Partition 2 of 2
other various small files.

T'anks in advance.

---

### Post by bruenig on 2007-02-04
Assuming these partitions are continuous, you should be able to use gparted, delete them and then create a partition out of the unallocated space.

---

### Post by TBOL3 on 2007-02-04
T'anks, it worked/

---

