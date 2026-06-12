---
title: "Hard drive detection issues"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by dmallo on 2008-07-18
I'm trying to install a copy of Ubuntu server on a home server box that I've built. Unfortunately, none of the install discs that I have tried seem to work.

The AMD64/x86-64 (or whatever you want to call them...) media would kernel panic on boot, while the 386 media would boot properly and work up to the point where the drive partitioning screen should have appeared. Instead of the partition screen, I get a message, "No disk drives were detected", and am presented with a list of possible drivers.

I'm not seeing either AHCI or ata_piix, the drivers that (AFAIK) ICH7 uses in the driver list either. :evil:

I'm pretty sure that it is not a problem with the drives themselves, or the motherboard. Both drives appear in the BIOS, and I can see both drives when I boot using a Gentoo 2006.1 live cd.

I am aware that the Realtek LAN chip on the motherboard can cause problems ([http://ubuntuforums.org/showthread.php?t=843398]("http://ubuntuforums.org/showthread.php?t=843398")). I tried disabiling the onboard LAN in the BIOS, and using a Netgear NIC left over from my previous server. However, this didn;t seem to have any effect...

Any advice you could give would be greatly appreciated. Thanks in advance.

The hardware I am using is:
Motherboard: D945GCLF (an Atom-based motherboard)
Chipset: Intel 945GC / ICH7
Processor: Atom 230
Hard Drives: 2x 320GB SATA2
Optical Drive: IDE CD-RW

---

