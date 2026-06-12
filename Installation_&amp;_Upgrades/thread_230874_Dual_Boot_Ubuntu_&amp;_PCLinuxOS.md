---
title: "Dual Boot Ubuntu &amp; PCLinuxOS"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by smasterson on 2006-08-06
I am dual booting winxp & ubuntu on 2 hdd (xp on master & dapper on slave). I want to remove xp & dual boot ubuntu & pclos. My question is, should I put ubuntu on the master & then install pclos, because I read in another forum that ubuntu's bootloader recognizes pclos easier than other way around. I'm a noob & any help would be much appreciated as it seems most of the dual boot info I found is on xp & linux. Thanks in advance:-D

---

### Post by linuxgeekery on 2006-08-06
It doesn't really matter which HD stuff is installed on. My recommendation:
Wipe XP off and install PCLOS. If the PCLOS bootloader doesn't recognize Ubuntu, follow [these directions]("http://doc.gwos.org/index.php/Restore_Grub")

---

### Post by confused57 on 2006-08-06
> **smasterson said:**
> I am dual booting winxp & ubuntu on 2 hdd (xp on master & dapper on slave). I want to remove xp & dual boot ubuntu & pclos. My question is, should I put ubuntu on the master & then install pclos, because I read in another forum that ubuntu's bootloader recognizes pclos easier than other way around. I'm a noob & any help would be much appreciated as it seems most of the dual boot info I found is on xp & linux. Thanks in advance:-D
First, I'd write down the exact entry in your  menu.lst for booting Ubuntu in case you need to add it to the PCLinuxOS grub menu. 
linuxgeekery is right, it'd be best to install PCLinuxOS over XP connected as the master drive...since Ubuntu fstab entries all point to hdb & connecting as hda may not be a good idea.
For reinstalling grub, if you need to:
 

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by smasterson on 2006-08-06
Thanks alot for your help linuxgeekery & confused57. I am going to try it right now. Again, Thank you very much :D

---

