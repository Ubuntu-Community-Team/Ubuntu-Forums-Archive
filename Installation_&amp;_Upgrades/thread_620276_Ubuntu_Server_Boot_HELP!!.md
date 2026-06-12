---
title: "Ubuntu Server Boot HELP!!"
date: 2007-11-22
forum: Installation &amp; Upgrades
---

### Post by f0xy on 2007-11-22
having a few problems booting from the newly installed system....

it all started towards the end of the Ubuntu server (latest release), when grub was being installed..... it did not want to install at all. The server is a Compaq proliant, 4scsi drives.... OS installed on /dev/ida/c0d0p1

it wouldn't install the grub boot loader onto the SCSI drive, so i thought il just put grub on a floppy and let it boot from that into the system.........then install grub to the drive when I'm into the system.

I made a floppy in another ubuntu system, using this tutorial - [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy) - The tutorial went through and everything worked....but i've no idea what to do once ive booted the problematic server from the floppy, i just get the grub prompt

cheers if anyone can advise what to do!!

---

### Post by scrooge_74 on 2007-11-22
I think you sould have a formated disk in the floppy at install time so grub gets installed there but the system files are in the hard drive.

Also I think instead of using the latest release for a server you should a stable release as 6.06 or a Debian stable release which should have less problems.

---

