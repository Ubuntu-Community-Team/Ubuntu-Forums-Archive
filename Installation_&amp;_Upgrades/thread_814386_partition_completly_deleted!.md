---
title: "partition completly deleted!"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by laxinon on 2008-05-31
OMG !
i tryed to install ubuntu from a winxp laptop.
to make a long story short, it completely deleted my partitions table (i guess i did something wrong..) and it took me about 4 hours to get back here using a Ubunto live cd.
i tryed active@ partition, it recovered the right partitions but will not write it (cuz i had only the trail ver)
any ideas on how to recover it now ?
no partitions, working form Ubuntu on a cd (i dont think i can install any thing..)
i have a usb disk on key but it is not bootable 

please help ...

---

### Post by Pumalite on 2008-05-31
Try systemrescuecd (it comes with TestDisk);
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
Post>
sudo fdisk -lu

---

### Post by Rallg on 2008-05-31
Don't panic. About two years ago, I munged my partition table (due to some other cause). With time and effort, I was able to restore XP and other things. It wasn't easy, but it was do-able. I don't recall what I had to do, so listen to Pumalite for better advice.

---

### Post by MQMike on 2008-05-31
Yes, follow Pumalite's tip to use TestDisk.
Read the TestDisk site for some excellent tips & guidance.
I've tested it on my machine and it worked (to test it, I intentionally deleted partitions and messed up the MBR).
Try not to write anything to that disk (it may overwrite good stuff you have lost on partition(s)), but even if you have, try TestDisk.

---

