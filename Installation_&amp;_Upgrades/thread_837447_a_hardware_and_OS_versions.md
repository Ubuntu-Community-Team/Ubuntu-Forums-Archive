---
title: "a hardware and OS versions"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by gejufan on 2008-06-22
i have a PC with two harddrive 20+60GB and a 256RAM memory. the computer is about seven years old and currently has Win ME installed on it.
which linux do you think i can install on the computer?
do i need to delete my OS inorder to install linux?
i have a wireless PCI card and on the package it says the card supports: Redhat, Debian, Fedora and SuSE OS, which one of the four would you recommand to install?

---

### Post by Habbit on 2008-06-22
The HD space is plenty for quite about everything, it's the memory what may restrict you a bit: any KDE-based distro, particularly KDE4 will be a resource hog. Also, forget about 3D desktop effects, since those eat tonnes of memory.

Your computer might be enough for running the plain Ubuntu distro (or another GNOME based distro), or, if you want slightly better responsiveness at the price of (in my opinion) a bit of ugliness, Xubuntu. The memory usage of "normal" Ubuntu depends a lot on what you use: I now have 14 firefox tabs open (with flash videos, etc.), plus Evolution, Pidgin and BOINC in the background, so memory usage skyrockets to 800 MiB. OpenOffice may also be a point of contention, but for "normal" use memory usage should not go much higher than 200 MB.

If you are a performance freak and don't mind spending a day or two on your computer, try Gentoo, which is a source-based distro in which packages are compiled in your computer to suit its particular specs instead of just making generic optimizations, so it may be able to reduce memory consumption. At first it seems too complex, but it is really easy and you don't need to know so much about system internals.

EDIT: please, don't flame me about how good and nice KDE is. I know it's good and I've used, but it _is_ (or at lease used to be, I don't know if the 4-final version corrected it) a resource hog, with memory usage ranging in the 300 MB with just Konqueror and Dolphin open

---

### Post by gejufan on 2008-06-23
hey here is some more hardware info:

CPU Type - Intel Celeron, 800 MHz (8 x 100)
Motherboard Name - Gigabyte GA-6OMM7E (3 PCI, 1 AGP, 1 CNR, 3 DIMM, Audio, Video)
Motherboard Chipset - Intel Solano i815E

Processor Properties:
Manufacturer INTEL
Version Intel - Celeron(tm)
External Clock - 100 MHz
Maximum Clock - 1200 MHz
Current Clock - 800 MHz
Type - Central Processor
Voltage - 2.0 V
Status - Enabled
Upgrade - 370-pin socket
Socket Designation - Socket 370

---

