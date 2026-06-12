---
title: "Resizing Partitions on a Compaq Presario R3210CA Notebook"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by cibby on 2007-07-02
I recently installed Feisty Fawn on my Compaq Presario R3210CA notebook... I struggled to install Ubuntu because GParted would not resize my Windows partition.

I read other users with similar problems, but there were few suggestions.

What worked for me: the brute force method.

The problem is that Compaq notebooks have a recovery partition hidden at the end of the drive; mine was about 750 MB. This prevents GParted from resizing it, even using the GParted LiveCD.

My solution was then to reinstall Windows. The Windows installer asks you to select a partition to install to, and also allows you to delete partitions. I did the following:

1) Deleted the recovery partition.

2) Resized the windows partition to 10 GB.

3) Installed Windows to the 10 GB partition.

After that, you're free to divide the unpartitioned space into partitions for Ubuntu, or anything else. Hope this helps anyone else struggling with this issue!

---

