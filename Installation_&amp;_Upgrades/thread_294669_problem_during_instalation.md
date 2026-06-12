---
title: "problem during instalation"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by otaviogomesbmx on 2006-11-07
im trying to install the ubuntu 6.06 on my pc. so i try to run the live cd.
it seems to be all normal, but then the screen turns black, i can even hear the initializing sound, but no images.

i have a nvidia gforce mx440 64mb, 256 ram, enough hd space... i dont know whats the problem.

---

### Post by Najand on 2006-11-07
Is it during the Live CD boot up or after installation? If it is the Live CD, select the second SAFE SCREEN mode and then try again.

---

### Post by otaviogomesbmx on 2006-11-07
its during the live cd boot, and i already tryed to run the safe mode.

---

### Post by taurus on 2006-11-07
Try using the alternate CD then...

[http://ubuntu-releases.cs.umn.edu/dapper/](http://ubuntu-releases.cs.umn.edu/dapper/)

---

### Post by test on 2006-11-07
I have exactly the same problem, on quite different hardware though. Why would the alternate CD help? The information provided on the "Alternate install CD" doesn't really describe our problem, or rather:

creating pre-configured OEM systems; (not really)
setting up automated deployments; (not really)
upgrading from older installations without network access; (not really)
LVM and/or RAID partitioning; (not really)
installing GRUB to a location other than the Master Boot Record; (not really)
installs on systems with less than about 192MB of RAM. (not really either)

Thanks for your help anyway.

---

### Post by taurus on 2006-11-07
> **test said:**
> I have exactly the same problem, on quite different hardware though. Why would the alternate CD help? The information provided on the "Alternate install CD" doesn't really describe our problem, or rather:

creating pre-configured OEM systems; (not really)
setting up automated deployments; (not really)
upgrading from older installations without network access; (not really)
LVM and/or RAID partitioning; (not really)
installing GRUB to a location other than the Master Boot Record; (not really)
installs on systems with less than about 192MB of RAM. (not really either)

Thanks for your help anyway.
Hey, the alternate CD is for those who experience problems with either graphic card or monitor!!!  So if you don't want to use the alternate CD instead of trying to get the LiveCD to boot, good luck.  And if you use the alternate CD, use the OEM option and after it finishes installing, it will tell you (on the screen) to run that command, oem-config-prepare, to create a user that you want to log in.  But if you use the Edgy, you don't even have to do that because it comes with a text base installer, first option on the CD.

---

### Post by test on 2006-11-07
Okay, it wasn't clear to me that the alternate cd is for problems like this, I'll give it a try, thanks!

---

### Post by taurus on 2006-11-07
> **test said:**
> Okay, it wasn't clear to me that the alternate cd is for problems like this, I'll give it a try, thanks!
Yip.  If you experience problems with blank screen or something similar to that with the LiveCD, then should try the alternate CD.

---

### Post by test on 2006-11-07
By the way, do I have in this case a chance when I try Dapper Drake instead of Edgy? I feel a bit reluctant to waste CD's with non-working installers... tia!

---

### Post by taurus on 2006-11-07
Not sure which one will work or they both would work.  With Dapper, you have to pick OEM and run an extra commend when it's done to create an account for you.  With Edgy, you don't have to since the first option on the CD is what you want to pick (while the second option is about the OEM).

---

### Post by sarwat on 2006-11-08
wel i have the same problem with the alternate cd it turns black during the installation n just stops and i tried on 2 different computers and 2 different cds and still the same, well i want to install ubuntu on my ext usb hard but no use cause of that

---

### Post by taurus on 2006-11-08
How fast did you burn the ISO image and what graphic card do you have on your machine?

---

