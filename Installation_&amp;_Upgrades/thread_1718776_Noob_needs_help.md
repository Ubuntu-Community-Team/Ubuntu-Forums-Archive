---
title: "Noob needs help"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by taylorjonasher on 2011-03-31
Just made the "test" switch from Vista on my 6 year old Inspiron 1501, AMD turion x64. Tired of MS, looking for something new, found Ubuntu Netbook remix 10.10(yay!) and wanted to try it out before I buy/build something new. Now here comes the problem...
 
Once it's installed (done it twice now), my home desktop screen does not load the side bar menu or the top menu bar. Just the default background is visibile. If you scroll the cursor over where the side bar menu should be, a half-assed "icon" appears (rectangular black box with a white box inside). I can click on these "icons" and pull up different windows (apps, control panel-ish looking screen, Firefox, etc..). But beyond that, nothing.
 
Also tried looking on the ubuntu site to check for system requirements for 10.10, didn't find any... it's possible I'm trying to throw a Lambo motor in a Vespa Ape body.
 
 
Any idearrrs?

---

### Post by taylorjonasher on 2011-03-31
By the way, I am assuming that I have downloaded and installed a/the 32 bit version of Netbook RM. Done some more snooping around Ubuntu.com to no avail.

---

### Post by jcolyn on 2011-03-31
My understanding is the netbook edition is a stripped down OS. I could be wrong though.

Instead of this OS I would go with the default 32 bit Ubuntu or Kubuntu (with 1 GB ram) They have more features. Ubuntu with the Gnome desktop runs good on my Inspiron 6000 so it should also work fine on your 1501.

Laptops do run better with at least 1Gb instead of the 512Mb most have by default.

At 256Mb video memory it should even run Kubuntu..

---

### Post by adamant_nz on 2011-04-20
I have this same EXACT problem and I too, am a noob.

I am running it on a Compaq Presario V2000. Is it possible that this computer is just too crap to handle Ubuntu?

Please help.

---

### Post by Hippytaff on 2011-04-20
Hi both
 
how much RAM and what graphics cards do you have?

---

### Post by adamant_nz on 2011-04-20
Hi there,

I'm not sure of the graphics card sorry but I know that it has 512mb ram and 128 of that is dedicated graphics. 

I decided to go for the netbook version because I thought it would run smoother than the proper full version of Ubuntu. What do you think, is there an easy fix to this kind of thing?

Adam.

---

### Post by Hippytaff on 2011-04-20
It depends...not a great answer I know. can you open a terminal (CTRL+ALT+T) and post the output of ```
lspci
``` That will tell us what graphics card you have.

---

### Post by adamant_nz on 2011-04-20
adam@adam-Laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
adam@adam-Laptop:~$ 


This was the output.

---

### Post by Zimmer on 2011-04-20
> **taylorjonasher said:**
> 
 
a half-assed "icon" appears (rectangular black box with a white box inside). I can click on these "icons" and pull up different windows (apps, control panel-ish looking screen, Firefox, etc..). But beyond that, nothing.
 
Also tried looking on the ubuntu site to check for system requirements for 10.10, didn't find any... it's possible I'm trying to throw a Lambo motor in a Vespa Ape body.
 
 
Any idearrrs?
Looks like you have encountered Gnome Do.. 

As it is a laptop try testing with 10.10 desktop 32 bit edition.(live CD , their purpose is to be able try before you install...)

I tried 10.10 on an old desktop that ran 8.04 fine and it was not a good experience s  l   o    w     and crashed a lot.
OTOH
(if you want something to quickly work as a Linux on that particular old machine and you think the specs are low , try Puppy Linux)..

---

