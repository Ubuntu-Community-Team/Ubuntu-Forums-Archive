---
title: "Ubuntu would not load after install / will load via live cd"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by rocky9191 on 2010-02-26
Hi,
I'm trying to install Ubuntu (9.10) on my sisters computer. I have installed ubuntu 9.10, but when I try to boot it from hard drive, it would stop loading a bit after the logo appears. The screen would turn off while the system is still running. Live version of Ubuntu works after reports of errors. I tried to search for the problem all over the forum, and could not find a good lead to figure out the problem. 

So far to figure out the problem, I verified if cd is corrupted. No issues there. Googled the problem, and seems like other users were able to install 7.04 (old posts). 

Its so weird though that live version works and the installed version does not.


Please help!

Here are my specs:

Processor: Intel Pentium Dual-Core [Mobile]("http://www.notebookreview.com/default.asp?newsID=3499&review=Gateway+MT3705#") Processor T2060 (1.60GHz, 533MHz FSB, 1MB L2 cache)
[Operating System]("http://www.notebookreview.com/default.asp?newsID=3499&review=Gateway+MT3705#"): Windows Vista Home Premium
Display: 14.1" Widescreen Ultrabright™ XGA TFT (1280x800)
Chipset: ATI Radeon Xpress 200M
Memory: 1024MB DDR2 at 533MHz (2 x 512MB), expandable to 2GB (total of 2 DDR2 slots)
Video: ATI Radeon® Xpress 200M Integrated Graphics
Audio: High-definition 2-channel audio
Hard Drive: 100GB PATA hard drive (4200 RPM) 
Optical Drives: 8x multiformat dual-layer DVD±RW drive
4-in-1 Digital Media Manager™
[Modem]("http://www.notebookreview.com/default.asp?newsID=3499&review=Gateway+MT3705#"): 56K ITU V.92 ready fax/modem (RJ-11 port)
Network: 10/100Mbps Ethernet LAN (RJ-45 port)
Integrated 802.11g [Wireless]("http://www.notebookreview.com/default.asp?newsID=3499&review=Gateway+MT3705#") LAN
Interfaces
[LIST]
[*]3 USB 2.0 ports
[*]VGA connector
[*]RJ-45 Ethernet port
[*]RJ-11 modem port
[*]Headphone/audio out
[*]Microphone
[*]Kensington lock slot
[*]AC adapter connector
[*]Synaptics Touchpad with Vertical Scroll
[*]Expresscard Type 54
[/LIST]

I can post logs, but I'm not sure which one is useful as I'm relatively new to this process.

-Mike

---

### Post by recluce on 2010-02-26
While many people here do not want to hear any criticism of Karmic (it is their holy grail), there seems to be an extraordinary number of problems with Karmic and ATI graphics. 

The LIVE CD does not start up with complete graphics support on all machines, so that might make a difference. A good sign that this is indeed the case would be a live session with lower screen resolution than what your hardware supports.

From what you write, I would assume that x.org does not start up correctly. Seach the forum for ATI, x.org and Karmic - you may find something helpful. Alternatively, see if Jaunty or Lucid work better for you.

---

### Post by cnntdygrhm on 2010-02-26
I'm having a similar problem. I'm trying to upgrade my netbook from ubuntu 8.04 to ubuntu 9.10 i downloaded the ISO downloaded the usb creator so that i could put it on my thumb drive, create the ISO and reboot with my freshely made ISO thumbdrive. When i reboot i get to the install screen select install and my netbook reboots and starts the process all over again without 9.10 ever being installed. When i select help i get the install screen but if at the very tipy top of my screen you see a 1/2in section that i cant read because it so small for help screen. I have a sylvania meso g netbook. please help

---

### Post by rocky9191 on 2010-02-26
Thanks recluce, I'll try other versions, and will report if any luck.

---

