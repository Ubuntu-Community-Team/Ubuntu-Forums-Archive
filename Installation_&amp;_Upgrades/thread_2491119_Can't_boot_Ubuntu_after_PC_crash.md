---
title: "Can't boot Ubuntu after PC crash"
date: 2023-09-26
forum: Installation &amp; Upgrades
---

### Post by soultanj on 2023-09-26
I run Ubuntu 22.04 as the only OS on my system and after a system crash, possibly due to overheating which has happened before but never resulted in difficulty booting the system afterwards, the system wouldn't show the grub boot menu. It does however show a windows light blue screen saying 'Your PC needs to be repaired' from which I can choose the UEFI boot menu option, which works, or go to startup settings, which doesn't work since I no longer have windows installed. The windows boot manager somehow still exists in the disk and UEFI recognizes it but it can't find Ubuntu installed on SSD as a boot option. Currently, I'm running a live Ubuntu 22.04 USB and it can open files on both disks, HDD and SSD.

Here's a paste from boot-repair:
[https://paste.ubuntu.com/p/M8vC24nvCK/](https://paste.ubuntu.com/p/M8vC24nvCK/)

---

### Post by Rubi1200 on 2023-09-27
Ubuntu 22.04 is on your HDD correct?

The SSD shows it contains the ISO image for 23.04; are you testing or is this the live medium you used to run the boot info script?

What is on sdc1?

Have you tried the default recommended repair to reinstall GRUB?

---

