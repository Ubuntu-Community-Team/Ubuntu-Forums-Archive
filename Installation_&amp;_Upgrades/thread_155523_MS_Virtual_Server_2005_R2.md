---
title: "MS Virtual Server 2005 R2"
date: 2006-04-05
forum: Installation &amp; Upgrades
---

### Post by battallion14 on 2006-04-05
Has anyone had any luck installing Ubuntu on virtual machine using virtual SCSI discs? I have been struggling for a couple days installing it on a Microsoft Virtual Server 2005 R2 virtual machine and kept getting a debootstrap error #2. I gave up on the virtual SCSI disc and it seems to be working fine with a virtual IDE disc but I am still curious to know if this has been a problem for anyone else.

TIA

---

### Post by reefland on 2006-04-06
I tried SCSI the first time as well and it hung at 31% trying to install core packages.

As you did, swithced to IDE and the install works great...  until you get the graphical login screen.  That comes up in a black widescreen 1600x600 garbled mess.  There is already a thread running about that issue [HERE]("http://ubuntuforums.org/showthread.php?t=156023&highlight=2005+R2").

Did you have that problem?

---

