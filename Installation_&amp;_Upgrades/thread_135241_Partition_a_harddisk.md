---
title: "Partition a harddisk"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by dag on 2006-02-23
Someone here who can help me ? 

I just install a new hdd. I have XP on hda (c: and D:) and want to install linux on hdb.
Can I use a part of the new disk on windows and make partition for linux.
Here is what I want:
On hdb I want to use 80GB for XP and the rest on 4 different partition (boot/swap/home/root)  I can get those working but I still have a 80 GB partition I cant do anything with. 
How do I set up this partition table ? witch is primary and extended and logic ?

Thanks for help

Dag

---

### Post by Robgould on 2006-02-23
Set whatever part of the new disk you want to share with windows and format it as NTFS. Windows will automatically detect this partition and allow you to use it after it is created. 
 
Leave whatever space you wnat to use for Ubuntu unformatted (Free Space). When you install Ubuntu select to install to largest freee space on that drive. Ubuntu will format and partition the freee space automatically. You can then edit it however you want from the install cd.

---

