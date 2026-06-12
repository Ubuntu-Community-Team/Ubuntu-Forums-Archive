---
title: "Lucid RC no boot  CD for Apple iMac 27in"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by binary10 on 2010-04-23
Lucid RC CD has broken X11 access on the Apple iMac 11,1 27in i7/i5.

It was working under the Beta 2 ([http://ubuntuforums.org/showthread.php?p=9161359#post9161359](http://ubuntuforums.org/showthread.php?p=9161359#post9161359))

'radeon.modeset=0 nomodeset' nolonger work on the casper boot.

Existing launch pad report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

The iMac 11,1 uses the - 4850 mobility I believe. Heres the OSX dump:

ATI Radeon HD 4850:

  Chipset Model:	ATI Radeon HD 4850
  Type:	GPU
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	512 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x944a
  Revision ID:	0x0000
  ROM Revision:	113-B9110C-425
  EFI Driver Version:	01.00.383
  Displays:
iMac:
  Resolution:	2560 x 1440
  Pixel Depth:	32-Bit Color (ARGB8888)
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Built-In:	Yes
  Connection Type:	DisplayPort
Display Connector:
  Status:	No Display Connected

---

