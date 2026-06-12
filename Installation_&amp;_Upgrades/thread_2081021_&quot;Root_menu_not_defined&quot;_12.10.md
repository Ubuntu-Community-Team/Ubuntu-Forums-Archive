---
title: "&quot;Root menu not defined&quot; 12.10"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by Stotto1119 on 2012-11-05
Hey, I am trying to install Ubuntu on a brand new hard drive but during the installation I am told that the root menu is not defined, I have done research but I don't really understand what to do. I don't know if you will need any more details but I'm sure I can find them.

---

### Post by dino99 on 2012-11-05
This is meaning that the partition for installing ubuntu does not have the "boot" flag set while formatting.

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by Stotto1119 on 2012-11-05
But do I have to create a new partition table or am I just looking in the wrong place all together?

---

### Post by darkod on 2012-11-05
When using the manual partitioning, and creating the root (main system) partition you have to give it mount point / (root).

Or if you are trying to use an existing partition, you have to click on it to select it in the list of partitions, and then the Change button below. For mount point select /.

Usually that message means that you haven't selected any partition with mount point /.

---

