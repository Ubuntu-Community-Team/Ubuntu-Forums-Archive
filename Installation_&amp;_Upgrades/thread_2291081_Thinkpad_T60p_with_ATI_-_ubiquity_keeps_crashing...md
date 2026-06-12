---
title: "Thinkpad T60p with ATI - ubiquity keeps crashing..."
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by netcom61 on 2015-08-17
Hallo                      -------------------    I've marked this thread as solved, though I've still not managed to install Ubuntu...  LinuxMint - Qiana - is working however, and is close enough to  "pro-level" OS to consider the matter reasonably resolved.

Trying to get Ubuntu 14.04, or 15.04 onto a T60p and absolutely no luck.
Ubiquity keeps crashing, telling me there's either a problem with the CD/DVD or the HDD...  can't write to disk...  
I've tried LinuxMint as well, and the same problem.
I've blanked the hdd with gparted beforehand but that makes no difference.
I've tried with nomodeset kernel parameter.
Currently downloading OpenSuse Live to try.
 

If anyone has any experience with the older T60p's, any solid lead would be appreciated... Thanks

---

### Post by ablinkin on 2015-08-17
are you using the side drive bay or the internal one?

---

### Post by netcom61 on 2015-08-17
internal... i think?   regular sata hdd...   oh, unless you're referring to the install media - it is a usb-flashdrive

The HDD is a Hitachi 100gb 7200rpm drive, however, when i look at it in Gparted, only 93GB are listed, and since this is a Thinkpad drive, which usually have a hidden restore partition, I'm wondering if that is what is preventing Ubiquity from writing to the drive.

---

### Post by netcom61 on 2015-08-17
Ok, got it figured....   had to switch off HiddenProtectedArea in Bios...   NOT!...

Still no joy... simply can't get anywhere with any of the ubuntu based CDs...   going to try an older version...

---

### Post by tgalati4 on 2015-08-18
So, I presume that you can boot off of the LiveUSB stick into a Live Session?  If so, then perform a "Check Media for Defects" during the GRUB2 bootup screen.  You may have errors on your USB stick.  I have a T43p and will be upgrading soon, so I will be watching this thread.

---

### Post by QDR06VV9 on 2015-08-18
**Just a thought** don't know if you have tried to use the installer after booting to the live session.
IE: the icon on the Desktop Install Ubuntu. And let the installer format the HD.(Should be ok now that you wiped it)
Some lappys are funny that that way.

---

### Post by netcom61 on 2015-08-19
well, it turns out this is just one funky machine to install on...  I've managed to get several different versions of linuxmint installed, the most stable of which, so far, are Maya and Qiana.  With those, it took several attempts at booting the same disk... turning off wifi via hardware switch while booting seems to help.

LinuxMint Qiana seems to be running very smoothly after updating and upgrading packages. 


The original issue was difficulty of getting live-CD/Flash to boot, then make it through the install process.

---

