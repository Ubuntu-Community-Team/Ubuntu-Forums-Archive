---
title: "This computer currently has no detected operating systems."
date: 2019-09-24
forum: Installation &amp; Upgrades
---

### Post by dave_in_roanoke on 2019-09-24
I have what I believe to be a fully functional and up to date win 10 PC.
I'm having difficulty installing Ubuntu in a duel  boot mode.
I get the following message at the “Installation type” stage.

"This computer currently has no detected operating systems.
What would you like to do?"

++++++++++++++++++++
I run into the same problem with fresh downloads of both
ubuntu-18.04.3-desktop-amd64.iso 
ubuntu-19.04-desktop-amd64.iso

---------------
Any guidance will be appreciated

---

### Post by yancek on 2019-09-24
Turn off fastboot and anything related to hibernation in windows.  Before beginning the install again of Ubuntu, read the documentation at the link below on dual booting with windows 10.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2019-09-25
To elaborate -- Win10 turns on FastBoot by default, which forces the Windows filesystem to remain mounted even when Windows is not running.  That prevents Linux from mounting those volumes, so it does not "see" Windows on the drive.

---

### Post by ubfan1 on 2019-09-26
From windows look at the disks and check that the partition type is not "dynamic".  Convert to basic if that's the case.  Dynamic is a Windows proprietary LVM which Ubuntu cannot read.

---

