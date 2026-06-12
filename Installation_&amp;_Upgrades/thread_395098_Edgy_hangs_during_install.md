---
title: "Edgy hangs during install"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Orinoco on 2007-03-27
I downloaded Edgy Eft 6.10 live cd iso, burned it to a CD, then ran the Live CD, and once the desktop appeared, and everything looked to be working, chose install.  Install seemed to run fine, until it was finished and I got a little message: "Be sure to remove the CD, close the tray and press Enter to restart."

Well, I removed the CD, (the install program thoughtfully ejected the CD) and pressed enter.  Nothing happened.  For a long time.  Finally I killed the power, and rebooted.  I saw the grub, and then the Ubuntu logo with the life sign tube, then the screen went black with a blinking underline in the upper left corner, then nothing.  Same thing happens when I boot from the CD and choose the boot from first disk option.

When I installed I chose to reformat the entire disk.  I am installing on an HP pavillion dv6000 laptop with 120 gig hard drive and 2 gigs ram, nvidia graphics and an AMD Turion 64 X2.

---

### Post by wpshooter on 2007-03-27
First, did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

Have you tried booting with the safe graphics mode parameter ?

If neither of these will work you may want to consider 2 things.

First consider getting the **KILLDISK** program and **WIPE** your hard drive completely clean and then attempt to install from the verified DESKTOP (live CD) once again.  Keep in mind that once you get the system installed you will probably need to update the drivers for your Nviidia card.

[http://www.killdisk.com/](http://www.killdisk.com/)

Or you may just want to consider downloading and burning and trying to install from the ALTERNATE (text based) CD.

Good luck.

---

### Post by Orinoco on 2007-03-27
Yes, I checked the integrity of the Live CD.  It's good.  

Booting in safe graphics mode also hangs, only with a message on the screen, sometimes.  One I wrote down was "Checking TSC synchronization across 2 CPUs:"  

I've got the NVidia driver install program, waiting for the rest of the system to work, since I've got a wide screen and everything is a bit stretched out under the standard install.  

I'll go take a look at killdisk.

---

### Post by wpshooter on 2007-03-27
P. S. - I notice that you apparently have 64 bit computer. 

If you are trying to install from 64 bit Ubuntu, you might want to consider dropping back to 32 bit for now, since I understand that the 64 bit may be a bit of a problem for now.

---

### Post by Orinoco on 2007-03-27
> I notice that you apparently have 64 bit computer. I thought so, too, but the 64 bit edgy release complained that it wasn't the right version for my computer, so I am using the i386 version.

---

