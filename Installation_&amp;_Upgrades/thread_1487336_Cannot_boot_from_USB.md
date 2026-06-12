---
title: "Cannot boot from USB"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by temporos on 2010-05-18
Hello.  This is irritating me...

I have UNR 9.10 installed on my EeePC 1005ha.  I installed 9.10 via a USB stick.  I downloaded the UNE 10.04 ISO, and I created a bootable USB out of it.  But when I insert the USB stick and restart the computer, the machine will not boot from the USB drive.

The USB drive is mountable, and I can browse the contents.  But the netbook always boots using the UNR 9.10 installation on the hard drive.  I checked the BIOS settings, and it looks for a bootable USB ("removable media") device before the hard disk.

When I restart, it reads from the USB drive (the R/W light on the stick flashes), but then it continues to boot from the hard drive.  Is there a known bug with the UNE 10.04 ISO?

---

### Post by temporos on 2010-05-27
**Solution: **ASUS programmed their BIOS such that you have to both set the machine to check removable media on startup, *and* you have to press Esc on startup to choose a boot device.  ASUS is synonymous with redundancy, apparently.

---

