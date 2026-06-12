---
title: "Installation problem"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by Mike0148 on 2012-05-13
I tried to install UBUNTU from CDROM on my Toshiba laptop and got message - No root file system is defined. Correct from partioning menu. What do I need to do?

---

### Post by darkod on 2012-05-13
If you are installing with the manual method, you have to select (or create) at least two partitions, the root and swap partitions.

The root partition has mount point / and is the main system partition. If you click on Next without specifying what partition should be used as root, it will give you that message.

Note that it's usually good practice to create a separate /home partition. You can find much information about that and partitions layouts on the internet.

---

