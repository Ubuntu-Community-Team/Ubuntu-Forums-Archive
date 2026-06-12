---
title: "Unable to start Ubuntu 9.1"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by kermit99911 on 2010-01-21
Please help ! I downloaded v9.1 and chose to install it within Windows (XP). It seemed to install OK, but when the installation was complete and the machine rebooted, I chose UBUNTU on the boot screen, but all I got was the following message "GNU GRUB v1.97 beta4 - minimal BASH-like editing is supported ... etc" and an input line " sh-grub> " What's happening, and how do I get by this to run Ubuntu? This is my first attempt with Linux, and I can honestly say, Im not too impressed. Now I have a menu on booting asking if I want XP or Ubuntu. Ubuntu wont boot, so, how can I repair or how can I get rid of this boot menu to return my computer to 'as it was' before

---

### Post by darkod on 2010-01-21
Wubi, or the ubuntu install inside windows, has it's problems. Why don't you try booting with the ubuntu cd, selecting Try Ubuntu option first, and see how you like it. It will run from the cd that way, not changing anything on your computer. Then if you decide you like it, just make a proper full ubuntu installation on its own partition and filesystem. Inside windows is not the way linux is supposed to work.

To remove what you did so far, boot into XP, go into add/remove programs and there will be "ubuntu" entry towards the end. Remove it just like any windows software. That will delete the ubuntu folder allocated to wubi and should also return your XP bootloader in the original state (no ubuntu entry in it).

---

### Post by kermit99911 on 2010-01-21
Thanks .. I have just uninstalled UBUNTU through the "ADD & REMOVE Programs" in the XP Control Panel ... and guess what ? The Boot Option is still there. It did not return my system to as it was. BTW, I did try the live disk first, thought about it, and then chose to install. How can I now return my MBR (?) to as it was before Ubuntu ?

---

### Post by darkod on 2010-01-21
Unfortunately that also happens. That's the problem when trying to combine windows and linux. And the reason why I always keep them on their own partitions, proper dual boot. :)

There is explanation here:
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

The part you want:
**How do I manually uninstall Wubi?**

 Remove C:\ubuntu and C:\wubildr*  
In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line.

I'm not so sure any more (been long time since XP), I think you have to enable seeing hidden files to see C:\boot.ini file. After that it is literary as simple as deleting the Ubuntu/Wubi line from it.

---

### Post by kermit99911 on 2010-01-21
Found c\ubuntu & c\wubildr, but cannot find c\boot.ini... I have enabled hidden files. Where else could this file hide ?

---

### Post by kermit99911 on 2010-01-21
Just done a search for boot.ini .. There is a copy (boot.ini backup) in the WINDOWS Folder.. Is it possible the wubildr file replaced the boot.ini and stored the backup ini file during Ubuntu installation ?

---

