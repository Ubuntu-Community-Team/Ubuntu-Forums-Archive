---
title: "Ubuntu Installation Hang before installation program can start."
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by snkboarder on 2007-04-15
Okay, so.  First the hardware.
AMD AthlonXP 3200+
2X512 Single-Channel DDR 400
2X36 GB SATA Seagate Raptor I's striped in Raid 0.
40 GB Maxtor IDE Diamondmax 9 on its own IDE chain.
Silicon Image ATA/133 controller with a DVD-Burner and a DVD-Reader, burner is faster and the master.
ATi Radeon 9800 Pro 128 MB.
550 Watt Antec Truepower PSU.
Asus A7v880 motherboard, with KT880 FSB.

So, I have Slackware 11.0 installed with LILO on the raid 0 drive and the maxtor is currently empty, and that's where I wished to test out Ubuntu since I have heard so many great things about it, especially in wi-fi detection and getting off the ground fast when installing new places.  

Here's what happens:

I pop in the Ubuntu CD that I burnt and verified afterwords.  I boot up, it loads, I select "verify disc" from the menu and it comes out with 0 errors in the checksums.  Then I hit "Install or Load Ubuntu" and it says it is loading a kernel and takes me to a screen with a progress bar with a bouncing bit in the middle that bounces back and forth for awhile before showing some progress.  After it hits 100%, my screen goes to a blinking line in the upper left-hand corner, my screen flashes, and then stays black, even though my monitor is on and recieving a signal.  I waited about 10 minutes the first time, then tried again in VGA safemode, and once again with the VGA setting to 1024X768X32 and waited a half hour.  Absolutely nothing. 

I disabled my RAID drive and made my Maxtor the main boot drive and no dice.  Tried installing from the other DVD-ROM.
I am unsure as of how to proceed.
 Unfortunately, since this installer is closed and GUI-based, I'm not sure how to debug it, or how to find out exactly what sort of error it is having.

---

