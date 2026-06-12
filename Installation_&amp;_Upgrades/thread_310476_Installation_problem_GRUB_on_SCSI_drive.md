---
title: "Installation problem: GRUB on SCSI drive"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by jackg on 2006-12-01
Description of a problem.

I am trying to do a fresh install UBUNTU 6.10 for a first time.
Installation fail due to GRUB installation error.

I have an old Pentium II dual XEON 450 MHz machine.
Adaptec 2960 Ultra wide SCSI card and Seagate SCSI 19Gb hard drive.
also I have an IDE CDROM and no floppy drive..

With this system configuration I have no problem to install SUSE 9.2, 10.1 Linux at all. It installs GRUB on MBR of a SCSI disk.

However UBUNTU is not able to install GRUB properly..

Partitions I have created:
/dev/sda1  - for /boot
/dev/sda2  - for swap
/dev/sda3  - for /

Default UBUNTU suggestion to install GRUB on hd0
I've tried that - installation of GRAB failed.
I've tried hd1, /dev/sda  - all failed.

(It usually show an error message when about 90% of installation completed)

What UBUNTU does different during the installation of GRUB, compare to SuSe ?

BTW. My PC BIOS not allowed to set SCSI as a second boot device.
(only as a 1st boot device)
With Suse I usually set CD_ROM as a boot device, and after, when the system after installation does reboot, I set my SCSI drive as a 1st Boot Device.

Please help.

---

### Post by jackg on 2006-12-02
I've finally solve this problem!!!
I was creating a separate /boot partition of size 8M - to small !!!!

During the installation of the when I was getting GRUB Installation Failer error message, I checked my partitions..

/boot was already 100% filled.


... So I restarted installation from scratch and made /boot 16M large.
Accepted default GRUB install to hd0  (MBR on the first drive)
Installation went without a glitch. Now /boot is about 68% used...

:D

---

