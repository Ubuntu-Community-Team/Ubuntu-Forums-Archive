---
title: "Error 17 - Cannot mount partition"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by dingooutback on 2005-06-16
2 hd

winxp on hd0 drive 1
ubuntu on hd1 drive 2

After 1st install grub gives error 17?

Please help, I change bios boot order to enable 2nd hard drive to boot first as i was not so keen on messing with xp at this early stage.

Thanks in advance

---

### Post by nvbauer on 2005-06-16
looks to me as if your reference to the hard drives are not correct

You have hd1 and hd2

I think they should be:
             hda1 = your first drive
             hdb1 = your second drive 

for all intents and purposes you can ignore the hd or sd, they only refer to the type of drive, what is most important is the last two digits, a1 and b1 for example. They refer to the physical drive (a or b) and the partion (1 or higher, if you have mulitple partitions on that drive). 

Hope this helps you understand better.

Norm

---

