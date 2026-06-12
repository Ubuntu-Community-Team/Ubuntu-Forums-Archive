---
title: "Ubuntu 10.10 live and install issues with 64-bit"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Keith Weisshar on 2010-10-11
I'm experienceing a slow boot issue when booting from the 10.10 64-bit CD.  It stays at the command prompt for a minute and then gnome starts at a blank background for a couple of minutes before the installer pops up.  The installer takes a minute to continue to the partioning screen after clicking forward and also stalls at installing system from downloaded package with progress bar at about 3/4 full on the installer screen.  I had the installer download updates during installation and also install third party software both checked.  I have an EVGA X58 3X SLI motherboard, 12GB of RAM, Core i7 920 CPU, EVGA Geforce GTX 470 video card and Acer H233H monitor connected via HDMI.

---

### Post by dino99 on 2010-10-11
is it frozen or you dont wait enough ?

sometimes we need to bypass some acpi or irq issue: on the boot line add either: irqpoll, nomodeset, noacpi, nolapic, noapic

---

### Post by dino99 on 2010-10-11
deleted: posted twice

---

