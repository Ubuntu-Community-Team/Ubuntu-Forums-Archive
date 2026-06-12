---
title: "Ubuntu made too many partitions"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by AGCSanthos on 2012-04-01
I am trying out ubuntu fr the first time and my Ubuntu installation disk made too many swap and unallocated space partitions. How would I delete these partitions as it gives me an error message "Please unmount any logical partitions having a number higher than X" depending on which partition I try to delete. Here is a picture of the partition:

[http://dl.dropbox.com/u/15380151/Partition.png](http://dl.dropbox.com/u/15380151/Partition.png)

---

### Post by navvirdi15 on 2012-04-01
re install your ubuntu again and delete your unnecessary partition

---

### Post by oldfred on 2012-04-01
You should not have to reinstall. But because you have swap in the extended you cannot unmount while in your install, so you need to use a liveCD.

From liveCD open gparted, you probably have to unmount swap(s) with swapoff as a liveCD likes to use swap to speed things up and delete sda6 and sda7. But check your fstab to make sure you do not refer to those partitions.

Not sure why or where that error is coming from, as you can have many more partitions than you have.

---

### Post by darkod on 2012-04-01
If I can add, you should be able to delete any partition that doesn't have the keys symbol next to it (which is not mounted in other words). You should be able to do this even from your hdd ubuntu running, not only from live mode.

But think first what do you want to delete and what do you want to achieve. Since all unmounted partitions seem to be towards the end of the disk, after deleting them you should be able to create one single large partition from that space.

---

### Post by chevy4x4grl on 2012-10-20
Thank you all for your wonderful knowledge.

---

