---
title: "Install Problems with 7.04"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by Carrot06 on 2007-05-01
I have built the following File/Torrent/Web Server from an old PC I had lying around:

Intel PII 350mhz
228MB RAM
PC100 M747 Motherboard
8mb Onboard SIS6326
8Gb Samsung 5400rpm 2mb Cache
PCI DWL-G520+ Wireless
PCI 4xPort USB2.0
PCI IDE ATA133
LG CED8080B CDRW

I have been trying to install from the Feisty Fawn Server and Alternative disc and am running into trouble either at:
**1.** the loading modules from CD section. the installer reports that my CD drive requires drivers or does not exist.
**2.** the partitioner does not pickup any available HDD
NOTE: In both cases only 1 CD drive and 1 HDD are connected.

The first error happens when the CD drive is connected to the onboard primary channel set as secondary, and the HDD is set as primary on the onboard primary channel. When trying to install like this the PCI IDE card has nothing plugged into it.

The second error happens when the CD drive is set to primary on the onboard secondary channel, and the HDD is set to primary on either the onboard primary channel or the PCI IDE primary channel.

I also know the CDs I have burned are ok because I have tested them on another machine and in vmware and both have worked fine.

Can anyone help me with this problem?

As a side note, I currently have the machine working with Edgy Eft, installed from the alternative CD. I also had an issue with this install whereby the installer would not pickup the HDD when connected to the PCI card, but once the install has completed I am able to connect the HDD back to the PCI card and it boots normally.

---

