---
title: "CD Boots then Installer Can't Find CD"
date: 2004-12-16
forum: Installation &amp; Upgrades
---

### Post by ycpdude on 2004-12-16
I am having a problem trying to install Ubuntu (Warty). I downloaded the iso, MD5SUM checked out, burned to disc. I then place the disc in my drive and it boots fine. I select language and keyboard setting then the installer tries to find the CD and says: 

"Your installation CD-ROM couldn't be mounted. This probally means the CD-ROM was not in the drive"

What in the world is going on? Why does the disc boot and then the installer doesn't recogonize the disc in the drive? Please Help.

ycpdude

---

### Post by Point-Zero on 2004-12-17
I also have the same problem.  The problem is that you probably have a SATA hd with IDE cd-rom (or in my case, IDE dvd-rom).

Here's some info:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=1440](https://bugzilla.ubuntu.com/show_bug.cgi?id=1440)
The interesting part is comment 42.

I was able to install Ubuntu, but it was broken beyond repair (well, at least for my limited knowledge). The last Debian installer also has the same problem, so I guess it means it still does not work in Ubuntu Hoary.

Not sure how this bug sliped into Warty release because I see 1 post a week about this problem.  Other distos (not based on Debian) seams to work fine.  That's a shame, because Ubuntu is working on my other all-IDE computer, and I want Ubuntu on this computer too!

Good luck.

---

### Post by cacofonix on 2004-12-18
I had this problem as well I managed to get it working by changing the settings in the bios. I have an intel 915p 82801 based motherboard. What do you have?

cacofonix

---

