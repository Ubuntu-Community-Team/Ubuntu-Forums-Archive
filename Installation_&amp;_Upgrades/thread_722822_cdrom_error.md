---
title: "cdrom error"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by AdHavoc on 2008-03-12
I just finished an installation of a CLI system for ubuntu 7.04, and when I try to "sudo aptitude install xorg", it says "Media Change: Please insert the disc labelled Ubunty 7.04 _Feisty Fawn_  -Release i386 (20070415) in the drive '/cdrom/' and press enter"  I have put in both the Alternate Install CD I used to install and an official Ubuntu 7.04 disc I got from Ship-It and yet it still comes up with the error.  When I installed it said it recognized the /cdrom/ fine so I have no idea what's going on.

---

### Post by TwoWordz on 2008-03-12
It's looking for the packages on the cdrom. 

You can edit /etc/sources/sources.list and remove the cdrom line. 

Then apt-get update and do your wizardry. :)

TW

---

### Post by AdHavoc on 2008-03-13
> **TwoWordz said:**
> It's looking for the packages on the cdrom. 

You can edit /etc/sources/sources.list and remove the cdrom line. 

Then apt-get update and do your wizardry. :)

TW

No, see, I NEED it to look for it on the CD.  I have no internet connection on the laptop so the CD is the only place to get the xorg package.

---

