---
title: "Wubi installer issues!"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by DuckyPowerUp on 2013-06-15
Having some big trouble with my dualboot. 

I love having a dual boot with ubuntu, so when I got my windows 8 laptop I installed Linux via Wubi (don't judge me, I'm really not techsavvy enough to juggle partitions so I chose the safe option). Somewhere along the way the linux part got damaged - when I tried to reset my password I got a "authentication token manipulation" error. "pwconv" did not help so I just want to try and uninstall and see if reinstalling will help.

As said I used a wubi installer, but somewhere along the line I must have lost the wubi.exe file because I had to reinstall it. Only issue is, when I start the wubi installer it offers to install instead of uninstall... And now I'm just kind of stuck. Any help would be greatly appreciated.

---

### Post by cwsnyder on 2013-06-15
You uninstall WUBI through your Windows Control Panel.  Look for Ubuntu in the add/remove program list, select it and uninstall.

---

### Post by lisati on 2013-06-15
To remove a copy of Ubuntu that you installed via Wubi, you should be able to do so via the Windows control panel, using the add/remove software option.  (Is that install/uninstall software in recent versions of Windows?)

---

### Post by fantab on 2013-06-15
WUBI doesn't work with 'Secure Boot' enabled Windows8 installation. This is probably the reason why WUBI was dropped from Ubuntu's latest 13.04 release.

You must consider real 'Dual Boot' with installing Ubuntu to its own partition.

Good Luck...

---

### Post by DuckyPowerUp on 2013-06-15
Yes it is, Lisati, but I can't find ubuntu or even Wubi in the list of installed programs...

---

### Post by DuckyPowerUp on 2013-06-15
Argh, talk about staring it in the face! I found where the Ubuntu part went, it snipped up my hard drive in two parts. I can see the Ubuntu partition in my file explorer under Hard Drives, but the wubi-uninstall file doesn't seem to be working... When I click it it asks permission to run then vanishes. Any suggestions?

---

### Post by lisati on 2013-06-15
It sounds like you didn't do a Wubi install, but did a regular "dual boot" installation.....

---

### Post by DuckyPowerUp on 2013-06-15
Oh dear. Would explain a lot. Back to google to find out how to remove that then, thanks for your help!

---

