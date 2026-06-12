---
title: "HELP!!! Recovery - can I reinstall completely from live or alt CD?"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by phuturism on 2007-01-21
Dear ubuntu-ers,

I managed to break a new breezy ubuntu install on a older laptop trying to upgrade ubuntu from breezy and switch to Xubuntu.   The problems arose when I interrupted some update/upgrade processes and then tried to rectify problems using the CDROM - don't ask me how but I did a great job of confusing this installation!   Currently it will boot but won't properly load the gui - after the login I get a nice ubuntu coloured screen but no action - no turning ubuntu wheel - but a mouse pointer that moves (so not a hang) but nothing else.  I can boot into recovery OK and type terminal commands but don't really know what to after that.  

I don't have data to lose on this machine so anything goes - BUT I cannot do a new install from a live CD because the bios won't recognise the USB CDrom drive.  I did the original install from windows using the great Instlux tool but I cannot even reinstall windows to go the instlux route  again because of the bios/boot issue.  I've been round the block trying to set up freedos boot floppies to load the proper usb CDROM drivers but no luck.  I've even tried doing a local network install using PXE from my working Ubuntu desktop but this was too tricky for me - I've only been ubuntu-ing for about two weeks!   I don't currently have net access from the machine as it "cannot configure network interfaces".

My question (s) - what can I do in recovery to salvage my installation?  Even better, can I just boot into recovery and reinstall from a CDrom?  The usb cdrom drive is accessible in recovery and I have a range of ubuntu/xubuntu install cds.  I can boot from a USB floppy drive but as described above I have had no success using this path to get either a new windows installation or an ubuntu installation.  

My desired goal is to have a Xubuntu installation on the laptop.

Please - any advice welcome as this has driven me mad all weekend!

---

### Post by phuturism on 2007-01-21
Anyone?

---

### Post by Sef on 2007-01-21
I would try a server install, then add the gui from the command line.  To do that, read [Psychocat's no gui]("http://www.psychocats.net/ubuntu/nox").

---

### Post by phuturism on 2007-01-21
> **Sef said:**
> I would try a server install, then add the gui from the command line.  To do that, read [Psychocat's no gui]("http://www.psychocats.net/ubuntu/nox").

OK - thanks for the tip!  

Hmmm..  that successfully identifies the CD and its contents using the 
> sudo apt-cdrom add 
from psychocat's guide.  It then mentions the source list and says "unmounting CD-Rom ... Repeat this process for the rest of the CD's in your set."

I disregarded that and pressed on...  
> sudo apt-get update
This fails as apt-get tries to use net repositories.  
> sudo aptitude install ubuntu-desktop
This fails as it cannot resolve dependencies - 16 conflict/broken dependencies it cannot address - "no solution found within the alloted time".

Is it possible to avoid repairing the installation and doing an fresh install using the CD from recovery/terminal?

---

### Post by Sef on 2007-01-21
> Is it possible to avoid repairing the installation and doing an fresh install using the CD from recovery/terminal?

That was a clean install.  I wonder if your cd is bad.   Check it when the boot into options come up.

---

### Post by phuturism on 2007-01-23
> **Sef said:**
> That was a clean install.  I wonder if your cd is bad.   Check it when the boot into options come up.

CD was OK but I was into dependency hell in a big way.

I did manage to do a netboot install from a win xp server so problem solved in the end.

thanks for your help.

---

