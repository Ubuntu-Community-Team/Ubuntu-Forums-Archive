---
title: "Partition Problem"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by rjt11890 on 2009-11-22
Im trying to install Ubuntu Netbook Remix on my new netbook so I made some free space on my hard drive by shrinking a windows 7 partition. When I try to reformat the free space into ext4, for ubuntu, I get a message saying that i have 4 primary partitions already and that i cant make any more. 2 are windows 7. The third one is my "EFI System Partition" and the fourth one is a 10 GB unknown. Which one should i delete to make room for ubuntu?

---

### Post by zvacet on 2009-11-23
On your free space make extended partition and then install Ubuntu on it.

---

### Post by Mark Phelps on 2009-11-23
> **rjt11890 said:**
> Which one should i delete to make room for ubuntu?

It's hard to say without more info.  Run a "sudo fdisk -lu" (that's a lowercase L, not a one) in a terminal and post the results back here.

---

