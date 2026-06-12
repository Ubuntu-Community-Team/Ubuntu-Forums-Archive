---
title: "livecd doesn't install -- goes to ash"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by mikelk on 2007-01-19
I've gotten the liveCD 6.06 LTS distribution and booted my Toshiba 3110CT with the x86 disk.  After choosing 'boot or install' or any of a variety of boot options, the farthest I can get is to a command line interface with the built-in shell (ash).  I can't make the thing install.  Can someone please tell me if I'm missing something obvious?

The only error I get is that it can't establish job control (some problem with tty -- I don't have it written down).

Any help is obviously greatly appreciated.


Mike

---

### Post by taurus on 2007-01-19
What's the spec of your Toshiba?  Maybe the LiveCD is having a little difficulty with your graphic card.

---

### Post by mikelk on 2007-01-19
> **taurus said:**
> What's the spec of your Toshiba?  Maybe the LiveCD is having a little difficulty with your graphic card.

Model name 	 Portege 3110CT 
Processor 	Mobile Pentium II 300MHz
Memory	128 MB
HDD 	20 GB
Display 	10.4 TFT 800x600
Display controller 	Trident Cyber 9525
Video RAM 	2.5MB
Sound 	ESSES1978
PC Card controller 	TypeII x2 Cardbus

I'm worried about the memory -- the doc on the CD sleeve says I need 256 MB...

---

### Post by SebMKd on 2007-01-19
Try the Alternate CD (can be found in the Download page). I don't know if it's a solution for you, but this worked for me. I had an old machine which wouldn't take the LiveCD, or at least never let me do the install and bugged at many stages. I knew the CD was good as I used it for my own rig. I knew I had enough RAM, and that my mobo, CPU, and graphic card were OK for Ubuntu. So changing the install process worked. The interface on the Alternate CD is more rough but not that bad... Note that I'm a NooB to Linux, but got pretty far and overcame any little bug in my way so far ;) 

Good luck!

---

### Post by taurus on 2007-01-19
With 128MB of RAM, you would be happier with the Xubuntu version since it's a little lighter on the system resources.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by Deived on 2007-01-19
I havent tried 6.06, but in 6.10 there is an install option when you boot the OS from the CD.  I dont mean doing an install during the startup of the CD, but rather once the Ubuntu is fully booted and running Linux off the CD there is an 'Install' icon on the desktop that will allow you to install to a disk.

---

### Post by mikelk on 2007-01-19
> **taurus said:**
> With 128MB of RAM, you would be happier with the Xubuntu version since it's a little lighter on the system resources.

[http://www.xubuntu.org](http://www.xubuntu.org)

I burned (at 4x) the xubuntu alternate install CD, and got as far as detecting my CDROM.  That is, I booted, selected an installation option (text) set local settings & keyboard then waited a lot while it tried and failed to find my CD in my PCMCIA drive.  This is probably the same thing that happened with the x86 ubuntu installation, since the CD never spun after the installer launched.  Is there a boot flag I can use to tell ubuntu that the cd is a pcmcia?  Do I need to move the cd to some other media (a USB drive, the hard disk)?

---

### Post by fishymark27 on 2007-06-26
I installed xubuntu edgy from the alternate CD by changing my Bios settings for my portege 3110ct. (You press escape at startup to take you to the Bios settings.)

It will install with the pcic setting, but once installed you need to change it back to the cardbus setting to get it recognised.

Also I updated my Bios from the Toshiba website too.

---

