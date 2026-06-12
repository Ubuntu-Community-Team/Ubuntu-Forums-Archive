---
title: "How to correctly install xubuntu on JFS filesystem"
date: 2015-07-06
forum: Installation &amp; Upgrades
---

### Post by temroa on 2015-07-06
guys a time ago i have installed xubuntu on jfs partition but after restart i got the grub screen not the operation system starting
how can i do this correctly

---

### Post by oldfred on 2015-07-07
Do not know JFS, but it must work as it has been tested in the past:
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

Grub also has a jfs.mod file for a grub 'insmod jfs' boot command to add the jfs driver.

---

