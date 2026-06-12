---
title: "Installing Linux on a Flash Drive?"
date: 2012-11-06
forum: Installation &amp; Upgrades
---

### Post by ilovemysillybanana on 2012-11-06
Okay so I want to know if it's possible to install linux on a flash drive, like actually on a flash drive because I'm not able to use the hard drive, so could I install it like off a cd or off another USB and install it onto another USB( with like 8-16 gigs ) so that I can have a computer I save things on to? 

I have a regular 8 gig flash drive and will go buy a 16 gig if necessary and I have a bunch of flash drives laying around, but again, the hard drive is not usable to me it's just so that I can do basic web browsing.

---

### Post by 2F4U on 2012-11-06
Why don't you use the persistence option when you create the usb flash drive? You can set the space reserved for documents and settings as you like. See picture in Step 6:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by Rex Bouwense on 2012-11-06
Yes you can.  Here is a procedure that I know works.  The version used is Lubuntu and old but the principle remains the same.
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
Also a quick search will reveal many other sites.

---

### Post by oldfred on 2012-11-06
Both of above suggestions are  good.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

If you want to do a full install it will fit in an 8GB partition. I have a full install in 8GB with another 8GB just for data on a 16GB flash drive. Not a lot of room, not speedy, but functional, if you have a fair amount of RAM. Do not install proprietary video drivers unless only using on one system.

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Actually an install to a USB flash device is the same as any install to a second drive with a few extra settings to reduce writes and improve speed a bit.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

