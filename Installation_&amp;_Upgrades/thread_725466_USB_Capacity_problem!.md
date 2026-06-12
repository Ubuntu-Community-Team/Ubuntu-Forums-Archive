---
title: "USB Capacity problem!"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by jiggyistheman on 2008-03-15
Hi to all, well I installed Ubuntu 7.10 on a PNY USB flash drive and then since things didnt go like I wanted them to, I am trying to restore my PNY USB back to its original capacity (4GB) now windows tells me it only has 725 MB capacity, I tried formatting it but still says the same.

How can I format it back to the original capacity?

---

### Post by Pumalite on 2008-03-15
Use Gparted Live CD:[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by jiggyistheman on 2008-03-15
Ok, is this easy to use? I just want to restore my PNY to its 4GB original capacity. Sorry to bother so much.

---

### Post by Pumalite on 2008-03-15
Boot with the Flash plugged in. In the right upper corner you can select drive. You'll recognize the 4 GB drive. Select it. Delete everything on it. Then make 'New' partition of 4 GB, formatted ext3 I guess.

---

### Post by jiggyistheman on 2008-03-15
Ok, I burned the newest version of the Live CD and booted from it but it gives me an error about FORCEVIDEO and that it couldnt open a graphical environment, besides when the CD boots there are a lot of options, wich one should I use?

Another thing, cant this be done with the ubuntu 7.10 Live CD?

---

### Post by jiggyistheman on 2008-03-15
Ok I need help with this Gparted Live CD, Does this takes a while to load or something? I use the first option (autoconfiguration) and then it tells me that no graphical environment could be loaded, then asks me to choose a Video thing so I use Vesa and then 800x600 resolution and then the screen goes black and nothing else happens, does it take long to load or what do I need to do to make it work.

My video card is an NVIDIA GeForce Fx 5200, does this matter?

---

### Post by tgalati4 on 2008-03-15
You can use the Ubuntu Live CD.  Go into a terminal:

>sudo cfdisk /dev/sdc

(Be sure to select the correct device name.)

To see what devices are connected:

>df -h

---

### Post by Pumalite on 2008-03-15
> **jiggyistheman said:**
> Ok I need help with this Gparted Live CD, Does this takes a while to load or something? I use the first option (autoconfiguration) and then it tells me that no graphical environment could be loaded, then asks me to choose a Video thing so I use Vesa and then 800x600 resolution and then the screen goes black and nothing else happens, does it take long to load or what do I need to do to make it work.

My video card is an NVIDIA GeForce Fx 5200, does this matter?

Did you use the option 'Force Vesa'

---

