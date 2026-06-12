---
title: "Trying to install 10.04 desktop, but the screen goes black after Ubuntu (dots) logo"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by boondocks on 2010-09-14
Trying to install Ubuntu 10.04 desktop (amd64) on this brand new system:
[INDENT]Processor & Memory:
[LIST]
[*]Studio AMD Phenom II X6 1035T Processor at 2.6GHz 
[*]16GB DDR3 SDRAM at 1333MHz (4 x 4GB)
[/LIST]
Graphics & Video:
[LIST]
[*]Dell ST2410 24" Full HD Widescreen LCD
[*]1GB ATI Radeon HD5450 Graphics Card with HDMI, DVI and VGA ports
[/LIST]
Rear Ports (all integrated):
[LIST]
[*]HDMI
[*]DVI
[*]Gigabit Ethernet Connection
[*]4 USB 2.0 ports
[*]eSata
[*]S/PDIF connector
[/LIST]
Operating System:
[LIST]
[*]Microsoft Windows 7 Home Premium 64-bit
[/LIST]
etc.
[/INDENT]
In other words, this system has:
[LIST]
[*]2 HDMI ports = 1 on the ATI card and 1 integrated
[*]2 DVI ports = 1 on the ATI card and 1 integrated
[*]1 VGA port = on the ATI card
[/LIST]
I connected the Dell ST2410 24" Full HD Widescreen LCD to the HDMI port on the ATI card and Windows 7 boots up just fine.

So then I put in the "ubuntu-10.04-desktop-amd64.iso" CD in drive and reboot the system.
I see the Ubuntu logo with the dots for a while and then the LCD goes black.
The LCD reports that there is no signal from the system.
The power light in front of the LCD goes from white to amber.
The keyboard stops responding.

I power off everything, remove the Ubuntu CD and reboot the system and it works fine again with Windows 7.

The CD has no problems.
At boot time, I checked it for defects and it reports no errors.
At boot time, I used this same CD to check the system for memory errors.  No memory errors.
I used the same CD to install Ubuntu on other systems and had no problems.

The 16X DVD±RW Drive has no problems.
In Windows 7 it can play CDs and DVDs.

What should I do?

---

### Post by mörgæs on 2010-09-15
Have you tried a live boot of 9.10 (or 10.10 beta, if you are ready for some experimenting)?

---

### Post by flick on 2010-09-15
Some good ideas for boot up options off the livecd at :

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by NT4usB on 2010-09-15
I have a (not so) similar setup. Intel VGA and HDMI onboard, Nvidia PCIe.
I'm using the binary Nvidia drivers, manually installed so consequently they break every kernel upgrade.
I have to go in to the BIOS, disable the PCIe graphics, and enable the on board graphics in order to get a GUI or terminal. Then I can reinstall the Nvidia drivers.

Although I really haven't given it a good try, I can't run the onboard Intel and Nvidia PCIe at the same time. 

When I first got the board, I tried in vain to get the on board HDMI to work, hence the Nvidia card... The dreaded 'No Signal' message.
Fortunately, the onboard VGA works so I use that.

So, short story long... might try installing using the onboard graphics, then sort out the PCIe once it's running.

---

### Post by boondocks on 2010-09-25
Thanks for all the responses.

Two solutions worked for me, at boot time:
[LIST=1]
[*]In Ubuntu 10.04, I removed the "quiet splash" options so that I could see the boot messages. I added the "xforcevesa" option.
[*]In Linux Mint 9, I selected the "Compatibility" mode.
[/LIST]
Either way, that (finally) got me to the Desktop.

---

### Post by mörgæs on 2010-09-25
Great. Please mark the thread 'solved'.

---

