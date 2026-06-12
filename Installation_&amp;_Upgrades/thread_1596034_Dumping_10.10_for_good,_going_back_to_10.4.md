---
title: "Dumping 10.10 for good, going back to 10.4"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by gadgetman1 on 2010-10-13
Since last Monday that 10.10 was release, I have been wrestling with this version to get it installed on my Dell Latitude D-800. It has left me with 3 days of agony & frustration. Over the past 3 days & nights, I have tried every option I could find on ubuntu forum as well as googled solutions. Non has worked.
The main issue is video driver & wireless. I can live without wireless, but not the video. In more details 10.10 does not work with nvidia graphic card & broadcom wireless.
I am using ubuntu since 8.04 Beta, & it has always worked out of the box. Ok, not exactly, with few exceptions of plugins & codecs, but nothing to this extend to be a major issue.
Even when I install the drivers (did that several ways), OS does not see them or when it sees the, it states I am not using them. When I try to use them get some other errors. I can go on & on with this, but I thin you got my point.

I give the same score to 10.10 release that I gave to Vista sometimes ago. I am going back to 10.4 which I have installed several times and works great.
Reading the forums, I feel even worse that many of you are going through the same torture, as I did.

My advise: 
************     DO NOT UPGRADE TO 10.10      ************

Applaud to ubuntu 10.10 team.

---

### Post by gordintoronto on 2010-10-13
What graphic card? What wireless adapter?

lspci will identify them. There are thousands of different nVidia cards, dozens of different Broadcom wireless adapters.

---

### Post by jcolyn on 2010-10-13
Did you do a fresh install or upgrade?

Some people have issues with upgrades while others don't.

I did fresh installs on both a Dell Latitude D-800 and Dell Latitude D-810 today. Both laptops are working fine with no issues.

I would suggest backing up all important file then wiping the drive. Then do a fresh install..

---

### Post by leclerc65 on 2010-10-13
10.04 gives me all I need.
No more 'the grass is greener on the other side' , thanks.

---

### Post by gadgetman1 on 2010-10-14
All Latitude D-800 have:
Nvidia GeForce4 Ti 4200 Go and wireless card Broadcom BCM4306.
I did a fresh install. There is definitly something with 10.10 different from 10.04 that these two devices don't work. Here is the output of lspci command:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

---

### Post by gadgetman1 on 2010-10-14
It was a fresh install. I never do upgrade of OS in any O.S.
I had already backed up my data & restored after re-installing 10.04.

---

### Post by everytimeref on 2010-10-14
> **gadgetman1 said:**
> Since last Monday that 10.10 was release, I have been wrestling with this version to get it installed on my Dell Latitude D-800. It has left me with 3 days of agony & frustration. Over the past 3 days & nights, I have tried every option I could find on ubuntu forum as well as googled solutions. Non has worked.
The main issue is video driver & wireless. I can live without wireless, but not the video. In more details 10.10 does not work with nvidia graphic card & broadcom wireless.
I am using ubuntu since 8.04 Beta, & it has always worked out of the box. Ok, not exactly, with few exceptions of plugins & codecs, but nothing to this extend to be a major issue.
Even when I install the drivers (did that several ways), OS does not see them or when it sees the, it states I am not using them. When I try to use them get some other errors. I can go on & on with this, but I thin you got my point.

I give the same score to 10.10 release that I gave to Vista sometimes ago. I am going back to 10.4 which I have installed several times and works great.
Reading the forums, I feel even worse that many of you are going through the same torture, as I did.

My advise: 
************     DO NOT UPGRADE TO 10.10      ************

Applaud to ubuntu 10.10 team.

I've got a dell D800 and had unsolveable video problems and went back to 10.04. I have to admit that after much fretting I did solve the wireless problem...... I pressed function f5 and it came on......!!!!!! still the legacy video driver thing is a bitch...

---

### Post by squish.the.bug on 2010-10-19
I'm feeling the same, actually. 9.04 was the last time my drivers worked completely on my Dell Latitude, so I'm thinking of skipping back to that.

---

