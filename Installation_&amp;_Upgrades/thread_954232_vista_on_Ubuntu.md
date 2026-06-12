---
title: "vista on Ubuntu"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by funk71 on 2008-10-21
Hello,
I'd like to install Win vista on a pre-existing ubuntustudio 8.04.
My HDD has already a partition, that you can see in the attached picture.
I think I should use the dev/sda1.
Does anybody can help me?
Thanks
Ciao

---

### Post by fongandrew on 2008-10-21
/dev/sda1 appears to already have some stuff on it. The simplest thing to do would be to move the data you have there to a partition on /dev/sda2. Then install Vista on /dev/sda1.

If, for some reason, you need to keep the dev/sda1 partition in its current location, you can use GParted to resize it. Then create a new partition in the freed up space and install Vista there.

---

