---
title: "Resize Ubuntu Partition"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by OOzypal on 2007-05-03
I have Ubuntu installed on my laptop (whole 80GB drive). I have sda1, sda2 and sda5.

I would like resize the Ubuntu partition to be 70GB instead of 80GB. I want to have 10GB of un-partitioned space.

I tried qtparted but the Resize command in the menu is grayed out.

---

### Post by louieb on 2007-05-03
Use the  [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php"). You can't  resize a partition if its mounted.  Using a  live CD gets around the mounted partition problem.

---

### Post by az on 2007-05-03
You can use the cd you used to install Ubuntu with, as well.  Just disable your swap first.  The Ubuntu desktop cd will boot and use a swap space if it detects one.

sudo swapoff -a

---

