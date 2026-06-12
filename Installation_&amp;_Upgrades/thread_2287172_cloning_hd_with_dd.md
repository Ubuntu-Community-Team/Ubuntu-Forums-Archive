---
title: "cloning hd with dd"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by user987 on 2015-07-17
i used dd in linux to clone my 32g ssd hd to a 120g hd.

The 32g had 10g used and 19g free space.

The clone 120g has the same #s, as the 32g hd, how can i expand i guess the partition from 19g free to about 100g free which is what the hd have?

Can someone give me simple step by step direction to do this i think in gpart?

Also the OS is win 7, so is there any special steps needed to be taken during the expanion?

---

### Post by VMC on 2015-07-17
Look up the 'man' page of  ***resize2fs ***

---

### Post by ubfan1 on 2015-07-17
Consider your partitioning scheme too.  No sense in just increasing the size of the last recovery partition.

---

### Post by sudodus on 2015-07-18
Please describe your partition table (the drive with partitions). For example, you can copy and paste the output of the following command into a reply and put it within [noparse]```
tags
```[/noparse]

```
sudo parted -ls
```

and it will be easier to give good advice.

---

### Post by user987 on 2015-07-24
HI to all,
             I solved the problem, in window i used a tool called mini tool partition and was able to expand the partition to capture the unallocated portion.

 Thanks to all  for your help and advice.

---

