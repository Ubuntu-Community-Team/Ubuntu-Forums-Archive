---
title: "Google.com/Chrome Crashes Ubuntu 12.04, Linux Mint 17.1 Possibly Ubuntu 14.04"
date: 2015-05-14
forum: MINT
---

### Post by smith-damianr on 2015-05-14
Hello. This problem happens on the Live CD or on a fresh installation. I searched quite a bit, all results were inconclusive.

Replicating this bug was quite easy on affected devices. Open Firefox, type google.com/chrome into the URL bar then boom. It crashes/freezes the system. The screen blacks out. It is not possible restoring the screen unless performing hard resetting.

MacBook 4,1

Ubuntu 12.04x64
Linux Mint 17.1x64

Notable hardware:
Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

---

### Post by frukt2 on 2015-05-21
I have got exactly the same bug. 
Firefox 
Mint 17.1
intel GM965 chipset

---

### Post by smith-damianr on 2015-05-22
Also, the Chrome web store causes the same issue, except switching hardware acceleration off (inside chrome's advanced settings) fixes the problem. That is a start. Also, I tried installing the latest Intel Graphics drivers for Linux. This was not effective.

---

### Post by MikeMecanic on 2015-05-27
It happen to me twice in the Vivid cycle under Opera 28 and  on a 3000Kbps Web site (NHL Gamecenter).  **Last Friday, on a fresh install after trying Windows 10 for a week**, I got the same issue with Ubuntu 15.04 Final release on Opera 29.  This time I took the time to see what is going on:  Trying to exit from full screen mode, the network switch or the graphics (not sure at 100%)) collapses and it ends in a black screen; was on a medium-low streaming (480p). In the black screen, the sound was still there (and I guess that video was there to) but I was dealing with a fully frozen desktop environment.  The only way to get out of there is this: **CTRL+ALT+F1.**  That brings you in the terminal and then you must do $ **sudo reboot**.  Things go back to normal after.

I thought that this problem was fix because I reported this issue to the Opera team...  That day I decide to try Rebecca Cinnamon and still with her.  Not easy to tame, she speaks a different language but she wears a nice gray scale dress.
Take care,

---

### Post by MikeMecanic on 2015-05-27
I have an important detail to add.  When I came back to Ubuntu after trying Win Ten alone, I used an old DVD installer: 14.04.1 LTS.  The first thing I did was to check in Disks Application if the LVM partitions were the same: The 14.04.1 LTS installer wash away Windows architecture, the partitions were the installer ones.  There always the same.  see screen shot.
Then I built a mkusb of Vivid Vervet and install it.  So Windows background is not an issue.

---

### Post by paul-louw on 2015-10-17
I also have the exact same issue on a system with the following specs:
HP Compaq 6710b
Firefox browsing to [https://www.google.com/chrome](https://www.google.com/chrome)
Linux Mint 17.1x64
Intel Mobile GM965/GL960 Integrated Graphics Controller

---

