---
title: "Dual boot, ubuntu first"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by flooperer on 2007-04-01
I have feisty installed on my whole drive. I need to go to a dual boot system. How do I set up my feisty install so that I can install windows afterwards?

Having big problems so far.

---

### Post by 1/0 on 2007-04-01
Basically changing partition sizes might fail so your best option is to do a backup of files and repartition the whole drive. There are some articles I found discussing how to change the partition size: [http://linuxmafia.com/faq/VALinux-kb/resizing-linux-partitions.html](http://linuxmafia.com/faq/VALinux-kb/resizing-linux-partitions.html) [http://www.terabyteunlimited.com/kb/article.php?id=132](http://www.terabyteunlimited.com/kb/article.php?id=132)

There are several guides on how to do the double installation: [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html)

The easiest is to set up a partition for Windows and install Windows in that partition (rest is blank). Then install GNU/Linux on the rest of the drive afterwards and last configure plus install GRUB in the MBR.

---

### Post by zvacet on 2007-04-01
[http://ubuntuforums.org/showthread.php?t=358183&highlight=windows]("http://ubuntuforums.org/showthread.php?t=358183&highlight=windows")

---

