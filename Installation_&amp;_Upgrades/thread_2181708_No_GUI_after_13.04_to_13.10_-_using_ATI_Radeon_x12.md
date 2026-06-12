---
title: "No GUI after 13.04 to 13.10 - using ATI Radeon x1200 Graphics"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by crasher2 on 2013-10-18
Hi Run the inplace update and when rebooted get the running in low res mode message Try to run in low res mode just hangs and goes nowhere. I was running the ATI Propriety driver v13.10.10 I tried the latest driver from the ATI site but it claims no hardware, although it shows up fine from 'lspci' as an x1200  (rs690m) Anyone know how to get this working again??
Thanks

---

### Post by heir4c on 2013-10-18
Start up from the recovery mode and try than in the little menu you will see: failsafeX
Or click just Enter when you in that menu and start further to the login/desktop. (If it will go to there) When you on the desktop, change in "Software&Updates to the open-source driver.

---

### Post by crasher2 on 2013-10-18
Just tried the latest beta drivers....they claim unsupported software and also tried the drivers that ATI recomment and they failed as no supported hardware??? I suspect the kernel is too new and ATI/AMD to useless to update drivers!! Is there some other open source drivers I could use....I have fglrx installed via apt-get but that doesn't seem to do anything either. grrr.

---

### Post by crasher2 on 2013-10-18
Hi Thanks but the same thing....just end up at low res mode and in just hangs

---

### Post by heir4c on 2013-10-18
Then you select the option for the root terminal and do a remove of the fglrx driver. There are more treads about removing fglrx, one link I give you here:
[http://ubuntuforums.org/showthread.php?t=2125753&p=12560321#post12560321](http://ubuntuforums.org/showthread.php?t=2125753&p=12560321#post12560321)

---

### Post by crasher2 on 2013-10-19
Hi Thanks, we are progressing....i think. After purging the fglrx driver I now start to get a GUI but it ends up a messed up screen. I tried re-installing the fglrx and it says -no supported adapters....so I removed it again. None of the amd drivers I have tried from the AMD site recognise my card either....very frustrating. Is there any generic type driver that might work??
Thanks

---

### Post by bianchirick on 2013-10-19
I had the same issue, I think it is a bug with lightdm. Revert back to the open sources drivers to get ride of the low graphics mode issue. Then, if you install GDM you should get to the login screen.

---

### Post by heir4c on 2013-10-19
If you go to "Software&Updates" and look for the last Tab than he search for the drivers automatic. After a while he will give you of possible drivers or say there are no drivers at all.

---

### Post by crasher2 on 2013-10-19
Hi This kinda worked....I installed GDM and then from a console it ran thru the config and booted me into the GUI. All looked good. However on the next reboot the login screen is all scrambled.Maybe I just need to do the windows thing and reinstall from scratch!

---

