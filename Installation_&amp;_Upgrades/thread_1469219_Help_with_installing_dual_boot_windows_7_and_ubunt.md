---
title: "Help with installing dual boot windows 7 and ubuntu 10.04"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by lilchunz on 2010-05-02
Hey everyone, 
I'm a pretty big noob with Linux but I've always had a fascination with Ubuntu and decided that I finally wanted to jump in to a new environment and learn more about this operating system. Well today I installed Lucid Lynx on a dual boot with a previously installed copy of Windows 7 and everything installed fine via Wubi...but now when I boot up and I get to my Boot Mgr and select Ubuntu I get the following message and can not get past a black screen stating - 

*Try* (*hd0,0*) [I]EXT2

I have tried to read what others have done to fix this but nothing has worked so far, if anyone could help I would be very grateful :)

Also I can still log into Windows 7 just fine, just no Linux...sad day!
 [/I]

---

### Post by Seti on 2010-05-02
Your best bet is always to install Windows first in the first primary partition. Remember to leave a bunch of space after this partition to put Linux, its always a good idea to have a separate /, /home and swap partition.
When you go through the Linux install with Ubuntu it will see the Windows install and you can select manual partitioning to set up your Linux partitions. It will then put grub in the MBR and you'll have your boot menu.

---

### Post by lilchunz on 2010-05-02
Ok thanks, checking this out now!

One alternative question, I do have a spare HDD....If I tried installing Ubuntu on it would I still get the same results?

---

