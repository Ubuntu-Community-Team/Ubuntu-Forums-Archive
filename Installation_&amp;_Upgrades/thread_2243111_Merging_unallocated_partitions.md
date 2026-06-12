---
title: "Merging unallocated partitions"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by alfirdaous on 2014-09-06
Hello everybody,

How can I merge the 3 unallocated partitions, I've got an error here:

[IMG]http://s11.postimg.org/vtib95ng3/Screenshot_from_2014_09_06_17_09_30.png[/IMG]


Thanks in advance

---

### Post by Vladlenin5000 on 2014-09-06
You can't *in this scenario* because the first part is indeed unallocated (and not a partition - you're using a misleading terminology) but the second chunk of unallocated space is actually inside an extended partition.

You need to remove sda3 first and then remove the swap partition also. Then you should have one continuous chunk of unallocated space after sda1.

---

### Post by alfirdaous on 2014-09-07
I removed the sda3 then the sda2 changed to swapoff then removed, both unallocated partitions are merged automatically (9.77 and 42.17 = 52GB), restart into windows, I shrunk the 52GB parition into 10 GB, need to have a shared partition between Ubuntu and Windows, then restarted into Ubuntu to create a swap partition 3GB.

[IMG]http://s14.postimg.org/wqh5yjg8x/Screenshot_from_2014_09_07_11_39_36.png[/IMG]

---

