---
title: "Dual boot - upgrade windows"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by tom91 on 2007-10-30
I have currently got a dual boot Ubuntu Fiesty - Win 98SE system, with each OS installed on separate hard disks. I need to re-install windows, replacing 98 with XP. Do I need to be careful to avoid messing up my dual boot system?

---

### Post by Pumalite on 2007-10-30
You are going to have a problem. XP needs to be installed first and needs to be in sda1. Then you reinstall Ubuntu after saving /home and data. You could just install XP on top of the other Windows and see what happens first. (make sure you backup everything first). With this last option, you would have to reinstall Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by tw0shoes on 2007-10-31
why does xp have to be in sda 1?

---

### Post by louieb on 2007-10-31
> **tw0shoes said:**
> why does xp have to be in sda 1?
It doesn't. For all practical  purposes XP needs to be on a primary partition. 
XP can be on the 1st or 2nd drive,  by itself or on the same drive with Linux. Here are some  helpful links.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902") [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") 
:lolflag:The 2nd link is quite complete. Herman has spent way too much time researching and playing with different ways to dual boot.
Just wondering are you installing XP fresh or do you have the upgrade CD?

---

