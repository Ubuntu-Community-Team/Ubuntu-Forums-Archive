---
title: "Ubuntu installion help"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by brobanmanx on 2011-01-15
Can anyone tell me how to install ubuntu dual-boot with Windows xp (PLEASE DO NOT GIVE ME THIS SITE [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) ) Like, what files i need and what-not. Right now i just have the ubuntu 10.4 and 10.10. Ive tried installing both but nothing is working. 
 
 
 
 
Also, im having a bit of a problem. whenever i try to open the installer i get an error message saying Windows - No Disk ''Exception Processing Message c00000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c" and i have to press continue a lot before it pops up. im not sure if thats the problem

---

### Post by Quackers on 2011-01-15
Are you trying to install Ubuntu from inside Windows. with wubi?
Is XP installed already and you want to install 10.04 or 10.10 to a separate partition to Windows?
Have you checked the MD5SUM of the downloaded iso files?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
How did you burn the images to disc?
You say that you tried to install both but nothing is working. What does that mean? Are the discs ignored? Do you get a black screen with a cursor?

---

### Post by bcbc on 2011-01-16
> **brobanmanx said:**
> Can anyone tell me how to install ubuntu dual-boot with Windows xp (PLEASE DO NOT GIVE ME THIS SITE [http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm) ) Like, what files i need and what-not. Right now i just have the ubuntu 10.4 and 10.10. Ive tried installing both but nothing is working. 
 
 
 
 
Also, im having a bit of a problem. whenever i try to open the installer i get an error message saying Windows - No Disk ''Exception Processing Message c00000013 Parameters 75b6bf7c 4 75b6bf7c 75b6bf7c" and i have to press continue a lot before it pops up. im not sure if thats the problem
Wubi doesn't like assigned drives that are empty, e.g. for card readers ([https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)). In general, unplug or disable anything you don't need.

Someone was asking about the pros and cons of Wubi vs a regular install today - it's worth a read [http://ubuntuforums.org/showthread.php?t=1667951](http://ubuntuforums.org/showthread.php?t=1667951)

---

