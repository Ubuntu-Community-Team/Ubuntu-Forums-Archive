---
title: "Dual Boot AHCI vs ATA"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by awacs on 2010-05-25
On a new Dell Vostro desktop, BIOS lets me set the controller to choose between AHCI and ATA modes. But Ubuntu Karmic cannot see the cdrom (although it will Boot From the First Hard Disk) with the BIOS set to ATA mode, and the install fails. It works nicely in AHCI mode. But Win2k server will not install in that mode, nor will it boot if already installed. 

How can I get the system to dual boot (without switching the BIOS back and forth)?

Thanks!

---

### Post by darkod on 2010-05-25
Hmmm... leave it on ATA and make a bootable usb stick instead of livecd? You can actually make it from the cd booted in live mode.

---

### Post by awacs on 2010-05-25
Actually, I was mistaken - it was Hardy, noty Karmic. A Karmic CD *was* able to install, and things are ok.

But, anyone know why Hardy wasn't able to see the cd - after booting from it! - in ATA mode?

---

