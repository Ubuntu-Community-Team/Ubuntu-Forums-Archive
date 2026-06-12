---
title: "xp wont boot"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by bobby2000 on 2007-12-22
ok, i went to emergency route and used xp recoevry console... nowwhenever i load up the computer, it just says "loading grump" or something, and restarts... HELP!

*edit : it says Grub loading agent, and then restarts

please help!

---

### Post by kellemes on 2007-12-22
> **bobby2000 said:**
> ok, i went to emergency route and used xp recoevry console... nowwhenever i load up the computer, it just says "loading grump" or something, and restarts... HELP!

Get into recovery console and enter " fixmbr" to restore the Windows bootloader.
Or use SuperGrubDisk to fix Grub,

---

### Post by bobby2000 on 2007-12-22
i think im unable to, i just get the packard bell screen offering me F2 ,F8, and then it goes to a black screen saying its loading grub, it then just restarts

---

### Post by Pumalite on 2007-12-22
Download Super Grub from here: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Burn the iso to a CD as 'image' and then boot from it. Do then as you were advised.

---

### Post by bobby2000 on 2007-12-22
thanks guys, once again the ubuntu comunity has been able to help :KS  I owe you one!

---

### Post by bobby2000 on 2007-12-22
i realise this isnt an xp forum, but... when installing xp, it hangs when i click enter on the "enter name and description" for computer bit.

---

### Post by kellemes on 2007-12-22
> **bobby2000 said:**
> i realise this isnt an xp forum, but... when installing xp, it hangs when i click enter on the "enter name and description" for computer bit.

Never heard of that actually..
I presume you're reinstalling XP from a clean disk?

---

### Post by Pumalite on 2007-12-22
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Delete all partitions in your hard drive. Make new partition of your whole hard drive formatted ntfs. Install XP. Boot Gparted again and resize your XP partition. Then install Ubuntu in the new partition. (it cannot be 'unallocated space')

---

### Post by bobby2000 on 2007-12-23
i don't have an xp boot cd as it came installed on the computer. Ideas?

---

### Post by Pumalite on 2007-12-23
Buy an OEM on EBay for ten bucks, and use the serial that came stamped on your machine.

---

