---
title: "Don't see a drive to install to"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by jchysk on 2011-02-28
I have Ubuntu64 10.10 on a USB stick. I go to Install Ubuntu, select language, and then when it gets to the part where you pick your drive there just isn't anything listed. I check GParted and the only thing listed is the USB stick. fdisk -i -u returns nothing.
There is a SATA hard drive that the BIOS detects and boots Windows fine.
I've tried:
sudo apt-get remove dmraid and then restarting the launcher
I've tried adding extra commands like:
acpi=force irqpoll
at boot.
I just want to completely format the drive and install Ubuntu, but if Gparted doesn't detect it I can't really seem to do anything.

---

### Post by pricetech on 2011-02-28
Check your BIOS for settings pertaining to compatibility of the drive controller.  Ubuntu may not be able to see the drive even though Windows can.

---

### Post by jchysk on 2011-03-01
Solution was physically switching drive from Sata3 to Sata2.

---

