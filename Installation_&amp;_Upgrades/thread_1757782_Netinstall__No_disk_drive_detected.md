---
title: "Netinstall / No disk drive detected"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by mat1z on 2011-05-13
Hi,
thank you for this nice forum. Really useful stuff for newbies like me :-)

After many hours trying to install Ubuntu(netinstall-64bit) i can not find any solution to get it working. I set-up via KVM and virtual device.

Installation gives me error "No disk drive detected" when trying to detect discs/hardware.
Someone told me i have to load *megasr-source_13.13.1021.2009-1_all.deb* by virtual-usb. It should include drivers for the controller not delivered by ubuntu-setup.
After that I got to next setup-step partitioning, but it only shows me an IPMI-device which is either the virtual usb or cd i suppose.

System is one week old and I got it with pre-installed debian64bit which is working fine. So i dont think its hardware causing this.

Hardware:
Motherboard Supermicro X8DTL-3F
Having two hard-disks, one SATA and one SAS.

This was a ready-to-use system so i have no clue how they got it to work - they want money for setting up a new OS. Since im a poor student i want to avoid paying :-)


Please tell me if you need any more informations!

Regards

---

### Post by Hedgehog1 on 2011-05-14
If your PC has a CD drive or can boot from a boot-able USB, you can download the ISO for the version of Ubuntu you need and make a LiveCD or LiveUSB. You can then install from that.

Do you have access to another system to create the media?


***The Hedge***

:KS

---

