---
title: "ubuntu installed, need"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by jeffhollon on 2008-04-15
alright, i have looked all over but can't find a step by step, but really need help.  I need to install full bore windows XP on my laptop.  I already have Ubuntu running great but have a hardware testing device that will not run in virtualbox or vmware windows XP.  I need to get Windows XP installed as a dual boot choice but am 1. afraid to mess up a good thing and 2. not exactly sure on getting it done.  Can someone give me a step by step run (or point me to one that already exists) on setting this up from partionioning to install and grub setup.  I really appreciate the help in advance.

also, one note, i have three partitions already one for home, / and swap (collectively taking up entire 80Gb drive).  Can i resize them to make room for Windows XP install without loosing anything.


thanks,
Jeff

---

### Post by dstew on 2008-04-15
You can do it. You will have to use a partition editor to shrink your Ubuntu home and/or root partitions to make room for XP. You can use the Gnome Partition Editor from a Live CD boot to do it. You cannot shrink a partition while your hard disk installation is running. I don't know how much room XP needs. You should create a primary partition for XP, it cannot function from logical partitions like Ubuntu can.

After you install XP on the new partition you created for it, it will overwrite the grub loader in the MBR without asking permission (it does not recognize that you have another OS on your computer.) You will have to re-install grub to create a dual-boot system. See this :[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by jeffhollon on 2008-04-15
thanks, that is the information i was looking for.

---

