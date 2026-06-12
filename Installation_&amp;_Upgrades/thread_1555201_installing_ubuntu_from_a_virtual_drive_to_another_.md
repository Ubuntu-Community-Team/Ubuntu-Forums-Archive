---
title: "installing ubuntu from a virtual drive to another physical disk."
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by amaruq_atka on 2010-08-17
I am currently using windows xp, but I have acquired another hard drive and wish to install ubuntu to it, unfortunately i do not have a working cd drive. I have loaded the newest iso in daemon tools and it asks me if i want to install it in windows, or restart my computer to do a full install. i wish to do neither. i want to install a full copy to my other drive with the virtual cd drive. I have found alot of help dealing with installing it on the same drive as windows or something that would require a floppy drive. this task seems like it would be alot simpler than installing on the same drive, buy maybe not. Did i miss a tutorial somewhere?

im not entirely new to ubuntu, but ive been without a computer for 2 years, so i may be slightly out of the loop. any help is appreciated! 	:smile:

---

### Post by uRock on 2010-08-17
Grub will have to install to the MBR on the first disk and you may run into issues with Ubuntu partitions not being on the same disk. To install without a CD ROM drive give [unetbootin]("http://unetbootin.sourceforge.net/") a look.

---

### Post by amaruq_atka on 2010-08-17
wow thanks! worked like a charm. ill remember this. u do rock!

---

