---
title: "I need to uninstall Mandriva!"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by avrilrox on 2008-05-10
Hey guys! I want to install Ubuntu on my laptop. I have Windows XP and Mandriva installed and i'd like to uninstall mandriva and run Wubi to install Ubuntu.

Can you guys please help me?

I'm using Mandriva's bootloader Grub

Thank you very much!

---

### Post by Partyboi2 on 2008-05-10
One way is to use a partitioning program like gparted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) and delete your mandriva partition and then resize your windows partition to use the unallocated space. Then run wubi.

---

### Post by mikewhatever on 2008-05-10
You have to restore Windows boot loader before deleting Mandriva's partition. There are several ways to do it, but do it first, then get rid of Mandriva.
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console](http://www.users.bigpond.net.au/hermanzone/p18.htm#Windows_XP_Recovery_Console)
[http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk](http://www.users.bigpond.net.au/hermanzone/p18.htm#Super_Grub_Disk)

---

### Post by avrilrox on 2008-05-10
Thank you! Ill see what happens!

---

