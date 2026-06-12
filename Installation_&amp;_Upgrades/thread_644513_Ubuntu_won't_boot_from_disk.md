---
title: "Ubuntu won't boot from disk"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by wranglers2 on 2007-12-18
Well, I'm pretty new to this, but here goes.  I just downloaded and burned Ubuntu Iso 7.10 to disk.   The disk seems to work while windows is running and I can view all the features etc.

When I shut down the computer and try to boot from the disc, I get the Ubunto graphic and then the main menu.  When I select instal Ubuntu it seems to work for a while.  The CD/DVD is spinning and the hard drive seems to be working, and things seem to be loading.  After a couple of minutes the monitor goes blank, then the computer seems to shut down or locks up.  I have to then reset the computer to go back iinto Windows.

I have a P5E motherboard, with 2 Gigs of memory, a Hitachi 1000K hard drive split into 2 logical partitions, and an NVIDIA GeForce 8600 GTS video card.

It may be the disk, but I have no way of checking, unless someone can think of anything else.  I burned the disk at high speed, but with the Samsung burner it should be O.K. 

Wranglers.

---

### Post by mikewhatever on 2007-12-19
Since it boots, but does not load the desktop, there is no reason to suggest that Samsung burner is bulletproof. Follow these steps:

1. md5sum check the iso [https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

2. Reburn at max x4 speed using a good quality CD.

---

### Post by logos34 on 2007-12-19
> **wranglers2 said:**
> It may be the disk, but I have no way of checking, unless someone can think of anything else.  I burned the disk at high speed, but with the Samsung burner it should be O.K. 

Sure there's a way to check the disk--select from the menu 'cd integrity check'.  And go back and verify the md5sum of the iso.

I routinely burn my install discs at 10x on cd-rw...never had a problem yet, but if everything else checks out you could reburn at lower speed.  

Otherwise try some [boot options]("https://help.ubuntu.com/community/BootOptions").

---

