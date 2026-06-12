---
title: "upgrade disaster"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by nuey on 2010-06-01
Hello all,
 
While upgrading to a newer version of Ubuntu I noticed a warning saying that the installation/upgrade should not be interupted. Unfortunately though, during this process my computer froze up and I had to shut it down. Ubuntu no longer starts on my computer. I still have Windows though, which is what I'm using now. I'm wondering if I need to completely remove Linux and reinstall? Any suggenstions/ info would be greatly appreciated. 
 
Thanks 
Nuey

---

### Post by bcbc on 2010-06-01
Do you have an ubuntu cd you can boot from and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/")?

---

### Post by peterpan7191 on 2010-06-01
You can try any of the following but I cannot assure you that they will bring back your system to your previous settings perfectly.

first find a live cd of the previous version you had.

1) use the live cd and backup all data into another drive which u will  not format during installation and re-install the previous version.
     You can backup whole home directory and replace it later on if you  have sufficient disk place (this brings back most of the desktop  settings , panel settings and start-up applications.)

2) Re-install the previous version in the '**SAME**' partition as of previous installation '**without the format option selected** **i.e. don't select the format option on the partition which already has ubuntu installed in it.**'. This retains most of the software and applications but does not guarantee the same with desktop themes, application themes, kernel updates and drivers.

3) If you can handle both things try combining both by backing up first the reinstalling and replacing things back to its place. else first is suggested (because second is said to give a random rate of success).

---

### Post by wisiwyg on 2010-08-24
Same thing happened to me trying to upgrade to 10.04.1 from 9.10 server. I have a mirrored HD. Would it be possible just to switch the sata data cables internally and reboot? It never completed upgrade.
TIA

edit: Solved problem by interrupting Grub, selecting recovery mode, selecting repair broken packages. After repair, rebooted and all was well.

---

