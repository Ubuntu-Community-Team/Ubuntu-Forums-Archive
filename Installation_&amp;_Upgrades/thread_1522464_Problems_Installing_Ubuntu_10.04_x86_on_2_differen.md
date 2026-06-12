---
title: "Problems Installing Ubuntu 10.04 x86 on 2 different Machines"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by DomiOh on 2010-07-02
Hi,
 
I've encountered serious problems installing Ubuntu 10.04 on two different machines.
 
Machine 1 is an AMD XP 2200+ machine with an elite group board and an ATI Radeon 3650 AGP graphics card and 1,5 GB RAM.
After selecting "Install Ubuntu" from the start menu, no splash screen appears, but I can see loading some things with the number of seconds used for that before the text.
After loading some system things the booting stucks and does not come back.
The same happens if I try to boot the CD as live version.
 
Machine 2 is an AMD 64 X2 6000 machine with a gigabyte board and an ATI Radeon 4850 PCIe graphics card and 8 GB memory.
After selecting "Install Ubuntu" the system boots up until the new background appears (the one with the "lights" on it) and then the system resets.
The same happens booting as live version.
 
The installation of old Ubuntu Versions (like 9.10) works without problems.
 
Has someone encountered the same or a similar problem or has someone a fix for that ?
 
 
 
Greets,
DomiOh

---

### Post by dino99 on 2010-07-02
tweak the boot line:

remove: quiet splash, to know what happen 
add: nomodeset and/or irqpoll, acpi=off, lapic=off, apic=off

---

