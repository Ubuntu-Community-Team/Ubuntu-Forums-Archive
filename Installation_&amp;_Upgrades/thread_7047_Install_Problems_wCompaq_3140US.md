---
title: "Install Problems w/Compaq 3140US"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by smiley on 2004-12-03
Hi -

I've installed i386 Warty on a Compaq Presario R3140US (AMD64), and I've run into some problems.

* My network connection will work for a few minutes, but will then cut out with "transmit timeout" errors.  From then on pings to my gateway return "Destination Host Unreachable".

* When I boot in normal (graphical) mode, the keyboard will lock and won't accept any input (but the USB mouse works).

* On the times when I can log in, the mouse will sometimes lock on me.

* Sound will sometimes cut out.

All of this screams hardware problems, but I'm unsure how to go about tracking them down.  I supply the "noapic" kernel option at boot time.  Also, Windows XP Home has been functioning on the system for months w/no problems, and the Ubuntu Live CD worked very well for me.

I've attached the output from dmesg, lspci, and lsmod below.  Any hints or ideas would be *greatly* appreciated!

---

### Post by wallijonn on 2004-12-05
It probably has to do with the nVidia controller chipset.

Do a search for nvidia. There might be others who are using your nForce3 mobo.

Is there any chance that you have a spare PCI NIC card? You could then turn off the on-borad NIC in the BIOS and use the PCI NIC to connect to the internet.

---

### Post by randy on 2004-12-05
You could try installing the AMD 64 version of Warty but these sound like similar problems that other people with AMD 64 laptops have had.

---

