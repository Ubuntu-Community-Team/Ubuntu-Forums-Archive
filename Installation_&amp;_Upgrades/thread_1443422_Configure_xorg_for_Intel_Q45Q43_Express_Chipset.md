---
title: "Configure xorg for Intel Q45/Q43 Express Chipset"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2010-03-31
We have a PC in the office to which I have been granted to install Ubunto 9.04 on it. It has an intel graphic card Q45/Q43 Express Chipset.

I will proceed with the installation in a 1-3 weeks but I am expecting to have problems related to the graphic card not being seen or not configured ok.

Can you tell me how to configure it and what would its xorg.conf look like ?

Until I do the installation, I can use the Live-CD to test out your suggestions or do queries.

---

### Post by Browser_ice on 2010-03-31
running from the live-cd 9.04, I see that the xorg.conf did not detect the intel graphic card. But then again, should it detect it when simply running the live-cd ?  Again, this is to find out what to do to make sure the intel video card will be configured once I install Ubuntu 9.04 (in 1-2 weeks once I get the ok).

...
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

> lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801JD/DO (ICH10 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)

---

### Post by Browser_ice on 2010-04-07
Anyone ?

---

### Post by Browser_ice on 2010-04-10
Since I got no answers, i'm trying this link:

HOWTO: Jaunty Intel Graphics Performance Guide
[http://ubuntuforums.org/showthread.php?t=1130582&highlight=Q45](http://ubuntuforums.org/showthread.php?t=1130582&highlight=Q45)

I think I had tried it before but I am doing it again.

---

