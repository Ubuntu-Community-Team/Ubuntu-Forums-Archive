---
title: "Demo Installation Problem"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by royzubr on 2008-06-16
I'm trying to start the demo option of Ubuntu 8.04 on a spare PC and part way through the load the pc goes into a loop displaying:
SQUASHFS error: Unable to read page, block 28e4a87d
SQUASHFS error: sb_bread failed reading block 0xa3959

I believe the CD is OK since it runs without problems on another PC.  When I log onto Windows and run the disk from Win XP and select the option to install to a folder under windows, the installation proceeds without problem.  In this mode the PC dual boot OK and I can then log onto UBUNTU.

I thought at first that there was a H/W compatability problem but now I'm not sure.  Any ideas as to what might be the problem installing without windows installed already.  The PC specs are:
CPU-AMD Athelon 64 3200+; MB-ASUS A8N-E; Memory-1024mb DDR Dual; Video-NVIDIA Geforce 7300GS; HD-WD IDE 80gb; Windows XP SP3

Steps Tried:
1. Install on freshly formatted HD
2. Install Windows XP /w SP3 & instal replacing Win XP
3. Run demo option from boot
4. install as a windows folder which worked OK.

---

### Post by hal8000 on 2008-06-16
> **royzubr said:**
> I'm trying to start the demo option of Ubuntu 8.04 on a spare PC and part way through the load the pc goes into a loop displaying:
SQUASHFS error: Unable to read page, block 28e4a87d
SQUASHFS error: sb_bread failed reading block 0xa3959

I believe the CD is OK since it runs without problems on another PC.  When I log onto Windows and run the disk from Win XP and select the option to install to a folder under windows, the installation proceeds without problem.  In this mode the PC dual boot OK and I can then log onto UBUNTU.

I thought at first that there was a H/W compatability problem but now I'm not sure.  Any ideas as to what might be the problem installing without windows installed already.  The PC specs are:
CPU-AMD Athelon 64 3200+; MB-ASUS A8N-E; Memory-1024mb DDR Dual; Video-NVIDIA Geforce 7300GS; HD-WD IDE 80gb; Windows XP SP3

Steps Tried:
1. Install on freshly formatted HD
2. Install Windows XP /w SP3 & instal replacing Win XP
3. Run demo option from boot
4. install as a windows folder which worked OK.


The squashfs is a compressed file system required to boot the live CD:

SQUASHFS error: Unable to read page, block 28e4a87d
SQUASHFS error: sb_bread failed reading block 0xa3959

The errors you are getting are typical of the optical drive being unable to read the CD. Although the CD runs on another computer, I think the either the CD/DVD optucal drive is either dirty and not reading the CD properly.
You could create another CD and burn it at a lower speed, or try the old plastic bag trick. Place the Cd in a plastic bag and place it in a freezer
-15C or lower for about an hour; take it out and leave it at room temperature for an hour.
This technique sometimes works, as it shrinks microscopic bits and burrs on the aluminium platter, which do not return once the CD reaches room temperature again.
In the past, I've had success with this on unreadable audio CD's and data CD's, hope that helps.

---

### Post by wpshooter on 2008-06-16
Are the BIOS on your motherboard up-to-date ?

Is the firmware on your CD drive up-to-date ?

---

