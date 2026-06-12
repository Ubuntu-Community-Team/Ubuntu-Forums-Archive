---
title: "Can't install ubuntu 9.10 to many partitions"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by pjani on 2010-03-25
Hy, i want to install ubuntu 9.10 on my HP nx9420. 

I left 48GB of unallocated space in between of windows and hp recovery partition.

I attached screenshot of GParted.

I need to make /dev/sda7 the home partiton

---

### Post by andrewthomas on 2010-03-25
What exactly did you try to do?  What didn't work?

---

### Post by oldfred on 2010-03-25
You only have 1 partition left and you need root (/) and swap or two partitions. You can shrink one of your logical data partitions by 2GB and set up the unallocated as root using manual partitioning.

---

### Post by Mark Phelps on 2010-03-25
An alternative would be to:
1) Move the HP Recovery partition to be adjacent to the first partition
2) Expand the start of the Extended partition to be adjacent to the moved HP Recovery partition
3) Add new partitions inside the unallocated area of the expanded Extended partition

But ... the concern I would have doing this is that the HP Recovery might then not work if you move it.

So, you should (1) Backup the HP Recovery partition to offline storage (you can use Clonezilla to easily do this), (2) Move the HP recovery partition, (3) test booting into HP Recovery to confirm that it still works.

Sorry, don't know how to do (3) since it varies by each HP machine.

---

