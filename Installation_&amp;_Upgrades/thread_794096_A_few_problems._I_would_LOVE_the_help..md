---
title: "A few problems. I would LOVE the help."
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by Eternaldeath on 2008-05-14
So, i've installed and run Kubuntu before on my old computer but recently upgraded. I have:

Intel E2160
GA-P35-DS3L
4xGB Corsair XMS2 6400
XFX 8800 GS 384mb
Antec Neo HE 500 watt
SATA LiteOn Optical Drive
160GB Hitachi Deskstar SATA

First, I tried Kubuntu 7.10 64 Bit and my screen just went blank and said [No Input] so I went to Kubuntu 7.10 32 Bit and tried to intall it but only got command line and no GUI. I had a live CD so i'm running that right now in Safe Graphics Mode. Then I tried to install it on my hard drive. First time it got to the end and then said there was a problem with Output/Input and it wouldn't finish. The second time it said it couldn't create the ext3 filesystem on my hard drive.

Then I tried to plug in my older IDE drive with windows so I could at get data off there or at least get something running for a bit it would boot fine but wouldn't recognize my IDE drive anywhere. Now if I have my IDE drive plugged in then I can never get past the mobo screen and I try to hit [Del] for setup but it's just stuck there. I couldn't access my SATA drive it said hal-storage-fixed-mount refused uid 999 so I tried enablizing SATA ACHI which I don't know about but read about that fixing some peoples problems and it fixed my access problem but, one point the installation with ACHI enabled stopped after some checks that all ended in [OK] and I could type but it was stuck there.

If anyone has any ideas let me know and i'll try to get any information you need. Thanks much.

---

### Post by dstew on 2008-05-14
Your first attempt at 7.10 with 64-bit sounds like a graphics display problem. Your other attempts seem to be frustrated by similar graphics problems. The hard disk problem seems more like a BIOS issue since you could not get past the motherboard display.

There are several ways to go here, and I am not sure which is the best. You might try an Alternate Install CD, and try 8.04 64-bit. The Alternate Install CD installs the same Ubuntu desktop system using a text-based interface. Sometimes 8.04 has better hardware drivers, and you might get a cleaner install. But, sometimes it is worse, you just have to try it. And, sometimes 32-bit is better than 64-bit on some systems (hardware drivers again), but sometimes not.

If you already have an Ubuntu system running, but can only get the command line, you might be able to re-configure the desktop display server with the command **sudo dpkg-reconfigure xserver-xorg** (for Gutsy.)

---

