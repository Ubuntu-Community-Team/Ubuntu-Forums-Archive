---
title: "Hangs at boot from USB"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by ColemanK on 2010-12-25
I wrote the ISO to a USB drive I had using the Universal USB Installer, and I put it into my new Acer Aspire One D255 netbook, and set it up so that it would be the first thing it booted to. I got past the ISOLinux loading screen, and now it's just hanging at a black screen with a bit of text:

Intel(r)PineView PCI Accelerated SVGA BIOS
Build Number: 2001 Accelerated PC 14.34 03/01/2010 02:34:31
DECOMPILATION OR DISASSEMBLY PROHIBITED
Copyright (C) 2000-2003 Intel Corp. All Rights Reserved.

Anyway, it's just sitting there. The USB stick isn't doing anything, it's not flashing or jittering, it's just slowly pulsating like it usually is when it's not doing anything. 

Any help would be appreciated.

---

### Post by C.S.Cameron on 2010-12-25
Try it in another computer.
If that doesn't work try using usb-creator from the Live CD or else UNetbootin.

---

### Post by ColemanK on 2010-12-26
It works in the other computer. Then I tried another Ubuntu variant, and it still didn't work, but worked on the other computer.

---

### Post by C.S.Cameron on 2010-12-26
Try UNetbootin?

---

### Post by gpecke on 2011-01-24
I had the same problem with an Acer eMachine netbook.

The bios will not tolerate the current or earlier syslinux versions, and always hangs with that stupid message. It seems not possible to make a bootable USB flash drive using the current syslinux. This seems to be a deliberate mechanism implented within the bios.

I damaged the hard disk boot using grub/grub2 on Ubuntu 10.10, which seems to have bugs, and
needed a recovery drive.

The only way to recover was to use a knoppix CD in a USB cd drive. The knoppix version must be
5.1.1 or greater, or it just hangs.

Safest thing seems to be to leave the Microsoft boot manager in place. In that case the machine runs
Ubuntu 10.10 perfectly.

---

