---
title: "Installing fiesta on external hard disc"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by shamreez on 2007-05-22
Hi,

I was installing ubuntu on my seagate 100Gb hard disc and i am facing a problem now.

I installed the OS on the external hard disc but the grub loader has been written on my Hp notebook.

Is it possible to load the entire grub loader on my external hard disk so that i do not see the grub loader
unless i plug in my hard disk (My booting seq is 1. CD, 2. External HDD. 3. Notebook HDD  I plan to keep Xp as far away from ubuntu as possible :D ).

If it is possible to do this then can some one please tell me how to identify the boot sector for my external HDD.

In Ubuntu my external hard disk is identified and (sdb) I tried loading the grub to SDB, SDB0 and SDB1 but the install fails at 98% when it is installing the boot sector :(.

Any help would be really appreciated

Thanks in Advance 
Shamreez

---

### Post by chacotaco on 2007-05-22
the big question is... what format is it? USB? eSATA? ePATA? SCSI? you get the idea... then we can help you figure out the right settings to use. another question is, do you have a USB jump drive that you can store GRUB on that can point to you external HDD. might be the easiest way. then no matter what computer you are on, you can always point it to the right place.

---

### Post by shamreez on 2007-05-22
It is a external USB hard disc (Sea gate 100 Gb)

Do i have to have another USB hard disc to store the mount points

---

### Post by misfitpierce on 2007-05-22
big question is what is fiesta? just kidding i know you meant feisty

---

