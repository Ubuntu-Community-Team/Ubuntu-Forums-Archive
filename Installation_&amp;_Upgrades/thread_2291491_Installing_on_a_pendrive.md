---
title: "Installing on a pendrive"
date: 2015-08-20
forum: Installation &amp; Upgrades
---

### Post by Novitk on 2015-08-20
I have a 16 gb pendrive and I'm willing to install Xubuntu 14.04.3 on it in order to have a mobile persistent installation that I can use in any public computer. I'll boot the PC with a second pendrive and install the OS in the first pendrive, just as I would if I was installing it to my HD. My question is: if I install it this way, will I be able to use more than 4 GB of my 16 gb pendrive? I read something that I would have to perform additional steps concerning the casper-rw file if I used Universal USB Installer. Do I have to worry about this if I don't install using Universal USB installer and I use the method I mentioned?

---

### Post by yancek on 2015-08-20
If you put Ubuntu on the flash drive as a Live CD with persistence, you would have to create the casper-rw partition with a Linux filesystem rather than FAT32.  You could also just do a standard install to the drive and would not need persistence.  A standard install will of course, take up more space on the flash drive than the Live CD.  Some info on this at the link below:

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)

---

### Post by Novitk on 2015-08-20
I intend to just do a standard install to the pendrive, so I guess I won't need persistence. Will my pendrive work in any public computer I put it, or will it only work on the computer I used to install Ubuntu to the pendrive?

---

### Post by yancek on 2015-08-20
The computer 'should' work in any computer that is capable of being booted by a usb as long as you do not install any proprietary drivers such as for your specific graphic card.

---

### Post by sudodus on 2015-08-22
The computer 'should' work in any computer that is capable of being booted by a usb, but there are complications with installed systems because of UEFI. It is difficult to make an installed system, that works in several computers (and in BIOS as well as in UEFI mode).

An alternative to an installed system is a persistent live system as described in these links

[mkusb version 10](https://help.ubuntu.com/community/mkusb#mkusb_version_10)

[One pendrive for all PC (Intel/AMD) computers - single-boot dual-boot multi-boot](http://ubuntuforums.org/showthread.php?t=2259682)

These persistent live systems use a ***casper-rw partition***, so they are not limited by the 4 GB max file size in FAT32.

Some time ago a made a portable ***installed*** system, that works in BIOS as well as UEFI mode. You can use the systems that I made or you can get tips from them and make your own system. Beware that there are problems with 'standard installed systems in UEFI mode', if you move the system between computers.

If you want a pendrive with a live and an installed system, that works in UEFI and BIOS mode, you can try 
[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506).

---

### Post by Skaperen on 2015-08-22
i did this a few versions ago on a netbook with the i386 32-bit versions.  the target USB memory stick looked like the boot hard drive just as if it had been a spinning platter (i did that, too).  now i make all my 1TB and 2TB USB backup drives bootable in case i need it during a recovery.  now i have 5 bootable [memory sticks]("https://www.google.nl/search?q=minnepinne&num=100&lr=&sa=G&hl=en&as_qdr=all&tbm=isch&tbo=u&source=univ&ved=0CDIQsARqFQoTCMCl8LavvMcCFUK9FAodmCoFEw") that i need to upgrade to 14.04.3.

---

