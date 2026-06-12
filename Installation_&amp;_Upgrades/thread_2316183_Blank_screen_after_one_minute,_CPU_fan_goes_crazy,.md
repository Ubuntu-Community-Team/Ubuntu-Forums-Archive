---
title: "Blank screen after one minute, CPU fan goes crazy, DOS of router"
date: 2016-03-05
forum: Installation &amp; Upgrades
---

### Post by oneillkza on 2016-03-05
Hi there

I'm having a fairly infuriating problem. I have a PC with a 1TB drive that is squealing, have bought a replacement, and am wanting to boot from a live disk to be able to dd the old drive across.

When I boot in, everything works fine, and I get to the desktop. However, after about one minute, the screen goes blank, the CPU fan goes to full power, the power/reset switches are non-responsive (I have to kill power at the PSU), and, as I recently learned, my wireless router gets overwhelmed and stops working until I power the box down (it's connected via cable).

This happens on the 14.04 live disk, but also happens when I try the Redo Backup and Recovery distribution (which is Ubuntu based). I've also tried a Mint live disk, which shows a splash screen, then after a few seconds, reboots.

I have tried all the boot options: acpi=off, noapic, nolapic and nomodeset. These don't seem to affect things.

I have checked in the syslog for the RedoBackup boot (I don't have enough time on 14.04 before the blank screen hits), and there are no error messages from previous boots when this happens.

The box itself works fine with the OSes I have installed already: Ubuntu 14.04, Ubuntu Studio and Win7. I have also managed to boot it from live cds in the past to get those OSes installed.

Specs are:

Graphics: NVidia GeForce 9600 GSO
Motherboard: Gigabyte P55M-UD2
CPU: Intel I5 750

Any help or alternate suggestions would be appreciated! Maybe I should just be booting off some kind of super-minimal, CLI-only distro to run dd, but it would be nice to know that I can boot from a live install disk for if I ever want to do a clean install on the box.

---

