---
title: "ATI driver issue in DELL studio"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by vamc on 2009-12-21
I tried to install wubi in Dell studio.It displays a message saying that the ATI catalyst drivers are missing as soon as I start a game.The game itself does not run normally.It gets stuck every second.Where can I get those drivers?


thanks in advance

---

### Post by Mark Phelps on 2009-12-21
Getting the drivers is not going to be the hard part -- getting drivers that will work with your device and Ubuntu 9.10 is an entirely different story.

Need to find out what ATI card/chip you have, since ATI dropped support for LOTS of cards/chips back in May, and (1) the drivers that work with the older cards won't work with Ubuntu versions newer than 8.10, and (2) the drivers that WILL work with the newer Ubuntu versions won't work with the old cards.

So, boot from an Ubuntu LiveCD, open a terminal, enter "lspci" -- and look for a line that mentions your video card/chip.  

Report back what you find.

---

### Post by Maheriano on 2009-12-21
I have the Linux version of the ATI Catalyst software running on my Studio.

---

### Post by vamc on 2009-12-21
> **Mark Phelps said:**
> Getting the drivers is not going to be the hard part -- getting drivers that will work with your device and Ubuntu 9.10 is an entirely different story.

Need to find out what ATI card/chip you have, since ATI dropped support for LOTS of cards/chips back in May, and (1) the drivers that work with the older cards won't work with Ubuntu versions newer than 8.10, and (2) the drivers that WILL work with the newer Ubuntu versions won't work with the old cards.

So, boot from an Ubuntu LiveCD, open a terminal, enter "lspci" -- and look for a line that mentions your video card/chip.  

Report back what you find.
i couldn't figure out the line regarding the  the video driver.. so i am sending you the copy of the complete terminal info..  

............................................................................




00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by vamc on 2010-04-18
Finally sorted out the solution for this problem. Just go to

System > Administration > Hardware Drivers.

If there is internet access, it would do the rest.

---

