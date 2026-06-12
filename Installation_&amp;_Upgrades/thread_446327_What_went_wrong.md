---
title: "What went wrong?"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by fkar on 2007-05-16
____________________________________________________
_Goal
Install 7.04, amd64.

____________________________________________________
_Configuration
AMD Athlon 64 X2 3800+
Gigabyte C51-MCP51 (VGA on board)
2x PC3200 (200 MHz), 512 MBytes, DDR
2x 200Gb (SATA2, raid0)
1x  80Gb (SATA2)

____________________________________________________
_Steps
The two hdd's of size 200Gb are in a raid, Windows XP already 
installed (don't really want to mess things up). So I tried to install 
Ubuntu on the 80Gb hdd. 
Using the installation cd, I took the following steps:
1) I installed the boot loader (GRUB) to a floppy disk instead of 
the MBR, ie, when prompted for grub location I entered (fd0) 
2) When installation finished (before rebooting) I run from a terminal
dd if=/dev/fd0 of=Ubuntu.bin bs=512 count=1
3) Saved this file to an external hdd.
4) Rebooted into Windows and added in c:\boot.ini the line:
c:\Ubuntu.bin="Ubuntu Linux"
5) Windows boot manager prompts, but when I choose
 "Ubuntu Linux" it only displays GRUB followed by a 
(crazy) blinking cursor.

____________________________________________________
_Question
What went wrong?

---

