---
title: "Can't install Ubuntu 18.04 on hp 15-DB0076NR"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by Vidorin on 2019-04-20
Hello everyone I come to you today with a problem and hopefully I can figure out a solution with your help. I purchased a new laptop since my HP-6510B is ancient and it was time for an upgrade. I have disabled secure boot and enabled legacy boot mode in the BIOS Ubuntu will not install correctly it appears. When I attempt to use the 18.04 disc there are a whole bunch of ACPI errors and blue tooth errors that pop up and the display screen is all wonky and you can't make anything out as the displayed image is unclear. It does have a UEFI BIOS and Windows 10 x64 is already installed on the machine. Also when I attempted to use my 16.04 disc a whole bunch of memory errors pop up while it loads and it wouldn't give me the option to install alongside windows therefore I didn't want to damage the boot manager and totally hose my system. I'm honestly lost and Ubuntu is important as I try to learn more about the software and it's a great game mastering tool as well. I appreciate any help that I can get so I thank you in advance.

---

### Post by dino99 on 2019-04-20
So you already have w10 and ubuntu 16.04 (gnome/kde/... ?) installed on that pc, right ?
Before adding 18.04, first glance at journalctl to know exactly what is wrong about errors/warningd, then fix them (i suppose you are able to dig the net finding similar issue and workarounds)
Also tell us how you have tried to made the installation, and which DE/flavour it is.

---

### Post by Vidorin on 2019-04-20
It won't let me install either one so it only has Windows 10 x64 at the moment.

---

### Post by yancek on 2019-04-20
Windows 10, if pre-installed on a GPT drive will be using UEFI so you need to boot and install Ubuntu UEFI also.  If you don't get the install Alongside option it may be that fastboot or hibernation are enabled in windows.  Turn it off.  Ubuntu has documentation on dual-booting with windows on UEFI at the link below so I would suggest you read that before beginning.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

