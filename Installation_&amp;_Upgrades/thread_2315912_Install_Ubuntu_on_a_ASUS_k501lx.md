---
title: "Install Ubuntu on a ASUS k501lx?"
date: 2016-03-03
forum: Installation &amp; Upgrades
---

### Post by sonlard_berglund on 2016-03-03
I have tried everything that i can find on the internet but nothing works.

I have enabled CSM and turned of secureboot but it still doesn´t work.

Anybody that know how to get ubuntu to work on this comuter?

I have windowss 10 installed on c: and i´m trying to install ubuntu on a partition e:, the c: and e: is not on the same harddrive. 

I want to be make a dual boot.

I made a USB boot stick with rufus USB, unetbootin and several other USB iso software but nothing seems to work.

I get to the Ubuntu screen and then the computer stops working and i have to restart.

Anybody that know how to get this owrking?

---

### Post by sonlard_berglund on 2016-03-18
anybody have an idea what to do to resolve this?

---

### Post by ubfan1 on 2016-03-18
You want UEFI mode, not some CSM compatibility mode.  The install media boots both UEFI and legacy, so CSM is letting the machine decide which, and maybe it's choosing the wrong one.  The second disk with Ubuntu probably should have gpt partitioning (not MSDOS partitioning).  That will eliminate problems with primary/extended physical/logical partitions, everything in gpt is primary.  Ubuntu has handled UEFI installs perfectly for years, it's the vendors who mess things up by adding non-standard restrictions, like specific names on the bootloaders or on the name in nvram to invoke them.  Asus did not seem to have any issues (on an x200), but do read up on UEFI

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

### Post by sonlard_berglund on 2016-03-21
thank you...will do that

---

