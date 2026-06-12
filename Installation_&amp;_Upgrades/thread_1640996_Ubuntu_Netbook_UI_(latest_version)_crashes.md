---
title: "Ubuntu Netbook UI (latest version) crashes"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by rwestover on 2010-12-08
Good Afternoon.

I acquired a Compaq N610c Laptop (Pentium 4 2GHz, 512MB RAM, 30GB HDD), a retired work station, and figured I would make it a rig to play on. I decided to install Ubuntu Netbook on it, as I wanted to get the best performance possible. This seems to have been a mistake, as I am experiencing the following symptoms:

-Every time I drag the mouse to the left hand side, the UI seems to crash (the bar disappears, the screen goes black, and then it comes back after a moment)

-Each time I bring up a system window (IE, shut down, restart) the window is completely black (though if I crash the UI by dragging the pointer to the left bar, I can see it for a fleeting moment and click in the appropriate spot to do what I need to do.

-I can no longer boot from the disk drive. I figured I would create an Ubuntu 10.10 disk and just format the partition and start it over, but even with my boot sequence set to boot from CD ROM first, I cannot for the life of me get it to boot to the disk (it always comes to the HDD). I'm still relatively new to the OS, so I cannot even do so much as get in to run the disk from inside the OS. Another odd thing that I noticed is that the disk drive eject does not work while in the OS, but while in to edit CMOS settings and during boot, it ejects just fine.

-The PCMCIA slots are not getting any power.

If at all possible, I'd like to try and fix the installation that I have, but any help at all would be much appreciated. The BIOS appears to be aged, and it does not have the ability to boot to USB. Thank you in advance!

---

### Post by rwestover on 2010-12-08
To clarify, I completely formatted the partition (I feel silly, because I know better) and this is now the sole OS on the hardware.

---

### Post by kerry_s on 2010-12-08
try to logout when in the netbook session, then select the desktop in the session menu after you select your user name.

---

### Post by lokipro on 2010-12-10
> **rwestover said:**
> Good Afternoon.


-Every time I drag the mouse to the left hand side, the UI seems to crash (the bar disappears, the screen goes black, and then it comes back after a moment)



I am have the exact same issue. I took a Latitude D600, completely wiped and installed Ubuntu Netbook, no partitions. 

I have a PentiumM / 1.80GHz / ATI Radeon 9000

Any assistance is greatly appreciated!

---

### Post by rwestover on 2010-12-10
> **kerry_s said:**
> try to logout when in the netbook session, then select the desktop in the session menu after you select your user name.


Thank you very much for your suggestion.

Unfortunately, this did not resolve my problem.

Is there a way that I am missing to boot from a system disk? At this point, I have tried both Ubuntu 10.10 and Windows XP pro discs (both are known to work, as I tried them on my wife's laptop). Again, I do have my BIOS set up correctly to boot from this device at start up. If it helps, I do have access to CLI within Ubuntu Netbook.

Thanks!

---

### Post by Lifonedg on 2010-12-19
[QUOTE=rwestover;10215880]Good Afternoon.

-Every time I drag the mouse to the left hand side, the UI seems to crash (the bar disappears, the screen goes black, and then it comes back after a moment)

Only 3 weeks ago I had a taste of Ubuntu and, after some further researching online, decided I'd try it on an old Compaq Evo D510s I had banging around my computer scraps. I popped in a clean NTFS formatted 120Gb HDD and installed the 32 bit 10.10 desktop version with a USB pendrive without any problems that I as a newb could detect in the last 3 days.

I too have experienced the same results after a seemingly successful installation of Ubuntu 10.10 Netbook on my Compaq nx9010 with XP Pro. (upgraded BIOS and CPU from 2.00 to 3.06mhz with 1GB of RAM). I experimented and booted from the pendrive (with HDD removed) to do a 'test run' without installing the Netbook version with similar results but dismissed the crashing as a bug from not doing a full installation.
(nx9010 BIOS does not list Booting from USB device as an option but without a HDD installed found the Ubuntu system on the pendrive)

I will be installing the desktop version on the laptop until the Netbook/Unity version has it's kinks worked out.

---

