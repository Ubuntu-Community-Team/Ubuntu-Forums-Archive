---
title: "Install from SD Card"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by bricin on 2007-04-18
I have a Toshiba Portege M200. It refuses to boot from the USB CD drive. It currently has Windows XP installed on a 20GB partition (~40GB free and unpartitioned).

I want to install Ubuntu in the remaining space and make this a dual-boot machine. The machine can boot from SD Card but I have been unsuccessful getting Ubuntu to install from there.

I have tried [http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html) these directions. I can now boot into something (I used the linux from an Edgy disk)  but a)cannot figure out how to mount the USB CD drive (USB appears to have loaded) and b)cannot get the network running.

Any help in getting the current boot loader to "see" the CD drive and run the Ubuntu installer from there or just to get the SD card bootable with Edgy (or if this takes a few days, Feisty) would be much appreciated. 

Thanks.

---

### Post by bricin on 2007-04-23
Okay, I found an alternate path by using [instlux]("http://instlux.sourceforge.net/"). It was a little rocky in that the network version died a few times (I suspect the mirrors were suffering under the Feisty Fawn ship-load).

---

### Post by mrbrown8 on 2007-07-08
I too have a Toshiba M200 laptop and wanted to dual boot Windoze and Linux. One thing I found out is that not all usb-based cdrom drives support booting. 

I have an Iomega 'Predator' drive (model CDRW9602) that won't boot discs, but later I got a Teac cdrom drive (model CD-210PU) that could boot discs. The Teac drive is what let me boot an Ubuntu disc and go through standard install.

I don't know what special feature you have to look for in usb-based cdrom drives that say 'I support booting', but it is something worth considering.

HTH

---

