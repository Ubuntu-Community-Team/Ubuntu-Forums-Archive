---
title: "Gateway laptop wont boot from USB stick"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by danatcsm on 2010-10-11
[LEFT]I recently decided to kick Vista to the curb and install Ubuntu on my Gateway laptop. I was able to install an old version of Unbuntu (9.1) from a DVD. I want to try out other distros, so I tried to use UNetbootin to make live installs on a USB stick. I have put several different versions of Linux on the USB, but my laptop will invariable not be able to boot from the USB. At startup, I get the boot menu and I select the "boot from USB" option. When the computer tries to boot from the USB, it always says "no operating system found."
I tested out the USB by booting another laptop (eeePC), and it is able to boot from the USB. I thought it might be a bad USB stick, so I tried to use a different one: same problem. 

In summary: 
I have used different USB sticks, different distros, different computers, and even different programs (Pendrive linux and UNetbootin). My Gateway laptop simply won't boot from a USB at all. 

The squirlly laptop is a Gateway CX210X, Centrino Duo, 3 Gb RAM, 160 GB HDD

Any ideas?  If I have to, I will simply edit the bootloader manually to boot from .iso files on my HD, but I would love to be able to use the USB to quickly try out other distros.
[/LEFT]

---

### Post by pricetech on 2010-10-11
Sounds like a problem with the laptop itself.

Is burning the other distros to CD an option ???

---

### Post by lechien73 on 2010-10-11
You could try a BIOS update to see if that helps with the booting issue. Otherwise, pricetech's solution is probably the best.

Welcome to the forums, btw :)

---

### Post by danatcsm on 2010-10-11
UPDATE:  

I was wrong about one thing: I was running 8.4. Anyway, I downloaded 10.04 LTS and burned it onto a disc. The computer booted into it and I installed it. Once again I tried to boot the Gateway into a USB with Partmagic on it, and got the old familiar "operating system not found." I am beginning to suspect that there may be an issue with the bootstrap firmware. Does anyone know how to check that?

---

### Post by oldfred on 2010-10-11
On my system it would not boot a flash drive from the USB even though it listed USB-floppy, USB-CD, USB-HD etc. But then one day I had USB flash in port and was rebooting a different hard drive and there it was. The USB boot choice did not work as it saw it as a hard drive. Go figure.

---

### Post by Mark Phelps on 2010-10-12
Just so you know ... according to Google, your laptop has both an Intel and Radeon graphics chips, but unfortunately, proprietary graphics support for the Radeon chip ended with Ubuntu 8.10.

So, when you DO install 10.04 or 10.10, if you plan on using the Radeon chip, you will be left with the open-source video drivers.  Don't download or force the installation of any other video drivers as they will trash your display, leaving you to boot into console mode to remove them and replace them with the default open-source drivers.

---

