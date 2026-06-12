---
title: "Can't Install Ubuntu 7.10"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by J.P. on 2008-01-09
This is the error that I get: 
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell(ash)
Enter 'help' fore list of built-in commands
/bin/sh: can't access TTY; job control turned off
(initramfs) 156.815018 hd b: no disk in drive

I have two 250 Sata hard drive.
This is my set up;
Intel Pentium E 2160-1.8 GHz
EVGA nForce 650i Ulta Rev 2
Mem 1Gx2/Crucial
A\: - 3.5 Floppy disk
B\: - Iomega Zip Drive
C\: - 19.5 GB - WinXP Pro
D\: - 106 GB - Where I want to put Ubuntu 7.10
E\: - 106 GB - 
F\: - 116 GB - Where I have all of my Windows programs
G\: - 116 Gb - Where I have all of my Games
J\: - 232 GB - External hard drive
H\: - DVD Ram Drive
I\: - USB DVD DRIVE
I think that is about it. Thank you for all of your help.

---

### Post by dabl on 2008-01-09
> **J.P. said:**
> This is the error that I get: 

(initramfs) 156.815018 hd b: no disk in drive

I\: - USB DVD DRIVE


I'll speculate that this USB DVD drive is the problem.  I don't know if you can install Linux with that setup.  If you have a BIOS option to allow "boot from USB device", make sure that is set to "YES", and make sure that your DVD drive is set in first position in the "boot device sequence" part of BIOS.  If you do those things, and the installer still can't find the DVD, you're probably done, unless you can wire in an IDE/PATA DVD drive for long enough to install the OS.  Once installed, it can probably be configured to read a USB optical drive, but the installer is not real smart about such things.  :(

---

