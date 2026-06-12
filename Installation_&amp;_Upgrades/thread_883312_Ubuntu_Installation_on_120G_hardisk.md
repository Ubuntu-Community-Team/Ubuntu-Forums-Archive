---
title: "Ubuntu Installation on 120G hardisk"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by kidman on 2008-08-07
I just installed Ubuntu on a 120G hardisk with any partition. Is it already to install Ubuntu on large hardisk without partition the disk? Would it causes any problem on the Ubuntu later?

---

### Post by spiderbatdad on 2008-08-07
You can use gparted live cd to shrink the partition at a later time if you want to add other partitions.

---

### Post by kidman on 2008-08-07
How do I do that?

---

### Post by spiderbatdad on 2008-08-07
download gparted live and burn it to a cd. Then boot up the cd. It will guide you through expanding, shrinking, creating, moving partitions. It has a very easy to use menu.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by sandysandy on 2008-08-07
have a look at the tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by kidman on 2008-08-07
Thanks, fella. I will try it. If any problem, I will post it.

---

### Post by kidman on 2008-08-09
Thank you very to you guys. It works very smooth and hassle free. Even non computer geek like me can partition the hardisk after installing ubuntu. I have divided my hardisk into three partitions.I didn't know there is such program available.

Thanks again you guys.:)

---

### Post by mikjp on 2008-08-09
> **kidman said:**
> I just installed Ubuntu on a 120G hardisk with any partition. Is it already to install Ubuntu on large hardisk without partition the disk? Would it causes any problem on the Ubuntu later?

It will not cause to Ubuntu any problems. But you should use three partitions for Ubuntu just to make things easier for you later. Use.

one for / 
one for /home
one for /swap

Having a separate /home makes it easier to install new versions of OS or other distro, as you dont have to format it. You can keep the existing /home and just add it to the new system.

Mikko

---

