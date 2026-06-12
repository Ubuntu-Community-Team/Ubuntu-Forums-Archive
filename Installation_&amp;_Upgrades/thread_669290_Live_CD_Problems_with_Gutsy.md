---
title: "Live CD Problems with Gutsy"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by kcummings on 2008-01-16
Hi,

I've read the existing threads about problems booting a Live CD, but I haven't found one that matches my problem.

I've installed Ubuntu Gutsy on my old Dell laptop with no problems and wanted to make a dual-boot setup on my desktop PC.  It's a homebuilt system with an ASUS P5W-DH motherboard, Core 2 Duo 6600, NVidia 8800 GTS video card, Seagate SATA HD.

I set the BIOS to boot from CD and restarted.  I got to the opening menu (start/install, install with safe graphics, etc.) and chose start/install.  The window popped up loading the kernel, then went to a splash screen with a slider bar going back and forth below a big "Ubuntu" logo.  While this was happening, the HD and floppy were running constantly.  After ~15 sec, the system went to a command prompt labeled "BusyBox v.1.1.3 Built-in shell (ash)" with a prompt that said "(initramfs)".

When I tried the safe graphics mode option, the same thing happened, except that, one the command prompt appeared, I got an error message: "ata2: COMRESET failed."

Does anyone have an idea what's happening here and how to deal with it?

Thanks!

---

### Post by Septh on 2008-01-22
I've been havig this problem, I fixed it by changing my hard drives from IDE mode to AHCI in the bios

---

### Post by kcummings on 2008-01-22
Unfortunately, my hard drive is already configured as AHCI.  Does anyone know if a particular component would be to blame?

---

