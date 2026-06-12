---
title: "Hangup Installing Ubuntu on Asus m4a88td-m/usb3 Mobo"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by kinsham on 2011-05-03
I'm asking some help on installing Ubuntu v11. I upgraded to this Asus mobo and find that it will not boot from CD or USB into the installer or Live CD. All I get is a hangup/black screen from either. The same result from Kubuntu and Gparted CDs.
 
The previous setup was an Asus P4PE mobo with a Pentium and that installed/ran Kubuntu just fine but slowly.
 
The config now is:
M4A88TD-M/USB3+AMD Phenom 555 (dual-core)+4GB RAM
4X WD SATA 500GB in RAID 5 using mobo h/w RAID controller.
1X WD SATA 500GB boot disk (C:)
CDROM - IDE slave
DVDR - IDE master
 
It boots/installs/runs WINXP perfectly, so maybe it's some hardware thing that Linux can't recognize and locks up. The CD/DVD also work fine under Windows so I don't suspect a h/w problem with those.
 
Any help or experience with this mobo/Ubuntu very much appreciated.

---

### Post by MattMc3 on 2011-05-03
Not exactly the same, but I have an Asus M4A88T-I Mini ITX USB3 motherboard. I haven't had any problems booting from the following live CD's: Ubuntu 10.04, Kubuntu 10.10, and Kubuntu 11.04. No problems with WinXP install disc, homemade boot discs, or USB thumb drives either. In fact, I've even been able to boot from an SD card/USB memory-card reader combo. My only optical drive is an external USB 2.0 Rosewill.

I can't think of why your setup isn't working. It shouldn't matter, but maybe try disabling your Raid setup in BIOS, disconnecting your HD's, or disconnect one optical drive at a time. Try and get a bare bones working setup then start adding things back in and see when/if it fails.

Matthew

Asus M4A88T-I Motherboard
AMD Athlon II X2 2.9Ghz CPU
Crucial 4GB (2x2GB) DDR3 1066 RAM
Western Digital Black 500GB 2.5" SATA HD
Rosewill External USB DVD-RWROD-EX003

---

### Post by kinsham on 2011-05-03
It may be solved. It seems to be a problem with the graphics chipset. This post
 
[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)
 
helped me along.
 
Checking nomodeset after hitting F6 during CD boot allows Ubuntu to continue installing.
 
I've yet to follow through and make the change permanent as per the link.

---

