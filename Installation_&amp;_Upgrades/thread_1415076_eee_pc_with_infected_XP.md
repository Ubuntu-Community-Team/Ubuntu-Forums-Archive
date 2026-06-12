---
title: "eee pc with infected XP"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by mikey47 on 2010-02-24
I have an eee PC 900A which I replaced the original Xandros OS with the nLite version of XP. After using it for almost a year, It is totally trashed with a virus that I cannot get rid of. I would like to go back to ubuntu, but not Xandros. Do I wipe or reformat the 4GB SSD before I attempt to intall?

---

### Post by darkod on 2010-02-24
No need, just use the Erase and use whole disk option in step 4 of the installer. That will wipe the whole hdd as it says.
But I'm not sure how Ubuntu would run on only 4GB. Maybe Xubuntu would be a better option. You might give Ubuntu a go first anyway.

---

### Post by dabl on 2010-02-24
I would use GParted, or "dd", on the SSD first, and nuke everything.  The original Xandros system used a small partition for recovery, and if you didn't already delete that, you might as well.

The 4G SSD is big enough to run Linux.  I have sidux with Xfce installed on my Eee PC 701, using ext2 filesystem and it runs just fine.  But you can't save much data there -- you'll need to use a USB stick or SDHC card for that.

For netbooks, I use an external USB CD ROM drive to install from. But, you can also make a bootable USB from a booted Live CD (on some other system that has an optical drive).  Then you can install from the bootable USB stick.

---

### Post by mikey47 on 2010-02-24
Thanks for the help. I'll have a clean machine in no time.

---

### Post by Sven6210 on 2010-02-24
You can even install the standard Ubuntu 9.10. I have installe the Ubuntu Netbook Remix on my EeePC 900a and it workd great.
 
The following two links will probably be of help for you in order to get everything to work perfectly:
 
1. The key for switching WiFi on and off:
[http://ubuntuforums.org/showthread.php?t=1295835](http://ubuntuforums.org/showthread.php?t=1295835)
 
 
2. Patching to make the microphone work well (usage of Skype, Ekiga etc.)
[http://ubuntuforums.org/showthread.php?t=1289061](http://ubuntuforums.org/showthread.php?t=1289061)
 
I hardly recommend the Ubuntu 9.10 UNR for your machine. I am running Ubuntu on my EeePC since April 2009 and I am very happy with it. And I have tried a lot of different distros such as EasyPeasy, EEEbuntu, Flux etc. Ubuntu meets my taste best - after changing from the brown desktop to a more greyish one ;)

---

