---
title: "Grub not loading at boot"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by Azzco on 2007-08-05
Okay that wasn't exactly true...I think, When I reboot my computer I get past bios and when I'm expecting grub to load I just get a five letter messege "GRUB".

I have no idea why it does this as grub never had any problems before, it began after I removed fedora and the boot partition (I realised that I never used fedora).I thought I'd just go for a seperate home partition and a root, here's my partition layout:
####
sda,
    sda1 /home 200gb
    free space 32gb
sdb
    sdb1 /media/WinXP 10gb
    sdb2 / 10gb
    sdb-1 free space 55 gb
    sdb3 swap 1gb
####
note:
Bios is set to load the second HD first

I have no Idea why grub won't load properly, afterall it displays GRUB so it should have found /boot right?

Should I just do a reinstall and make a boot partition on my USB Flash memory instead?

---

### Post by Pumalite on 2007-08-05
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or follow this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Re-install Grub to the MBR (hd0,0)

---

### Post by Azzco on 2007-08-05
Thanks for the fast reply, I'm a bit confussed over what HD my /dev/sdb is recognised as by grub during boot though... I'll just try to go by that guide :)

---

### Post by Azzco on 2007-08-05
Okay that didn't really help, I'll try editing my bios to boot from the other HD first.

---

### Post by Pumalite on 2007-08-05
MBR usually in sda1. sda is whatever your BIOS sees as 1st.

---

### Post by Azzco on 2007-08-05
Oh okay, well I still can't get it to boot from my machine... Going to try out supergrub and see if that helps... I just think that it's weird as it's worked perfectly before =/

---

### Post by Pumalite on 2007-08-05
Take a look with this: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Azzco on 2007-08-05
I think I got SGD on my USB Stick now, just going to try it now :)

---

### Post by Azzco on 2007-08-05
Okay this doesn't get me anywhere, the SGD did indeed boot but there wasn't any english language on it and several options didn't work, I'll just reinstall ubuntu on the last gbs of my first HD and see how that goes...

---

### Post by Pumalite on 2007-08-05
Make sure you install Grub to the MBR (hd0,0). Step 7>Advanced Tab>(hd0,0)

---

### Post by Azzco on 2007-08-05
Now this was odd... I went through the grub guide you linked on the livecd, no fix but when I enterd commandline from the SGD and used the same commands it worked all of a sudden. :D
So now my kubuntu is back in action but needs a few 100 mbs downloading of apps to stay up to date. Great thanks for the help Pumalite :)
If nothing else I've learned alot from this experience ^^

---

### Post by Pumalite on 2007-08-05
You are welcome. Enjoy and good luck. May Ubuntu be with you!

---

