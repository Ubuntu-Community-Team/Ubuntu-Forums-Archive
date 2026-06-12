---
title: "HP Mini 311 will not recognize bootable USB key"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by linkylingtoncarl on 2012-10-04
I have an HP mini 311 that has recently undergone a factory restore (to Windows 7) from the recovery partition. I previously had a dual-boot setup of Ubuntu 11.10 and Windows 8 RP (eek!). 

Given Windows 8 was a complete mess imo,  I wanted to do a clean install of Ubuntu. The new Windows 8 boot configuration was making this extremely difficult, hence the factory restore.

 After the restore,  when I try to boot a 12.04 USB image my boot loader cannot even recognize that the device is there. I have tested the same image on a different computer and it worked fine recognizing the device and beginning the installation process.  My HP mini also recognized a USB image when I had originally installed 11.10. Is there something that Windows 8 may have permanently changed in my boot settings that would disallow me to boot from a USB device? (I have also used wubi to write an entry to the MBR, to no avail.)

---

### Post by bcbc on 2012-10-04
You don't use the MBR to boot a USB stick. It's a BIOS function: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00364979&tmp_task=setupCategory&lc=en&dlc=en&cc=us&product=4071240&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00364979&tmp_task=setupCategory&lc=en&dlc=en&cc=us&product=4071240&lang=en)

Wubi won't write to the MBR (lucky for you, or else you wouldn't be booting Windows).

---

