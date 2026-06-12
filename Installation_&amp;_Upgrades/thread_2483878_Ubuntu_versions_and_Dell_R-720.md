---
title: "Ubuntu versions and Dell R-720"
date: 2023-02-11
forum: Installation &amp; Upgrades
---

### Post by kdmiller45 on 2023-02-11
I have a Dell R-720 Server Ubuntu 16.04 installs with no issues, but anything newer Bombs
what changed between these versions that they will not install, can't even get to loading the install screen

Keith

---

### Post by grahammechanical on 2023-02-11
What changed between Ubuntu server 16.04 and server 18.04? The Installer.

> [FONT=serif]Ubuntu Server 18.04 LTS introduces a new installer, the "live server" installer (sometimes called "Ubiquity[/FONT]
[FONT=serif]for Servers" or simply "subiquity") which provides a more user friendly and faster installation experience.[/FONT]
[FONT=serif]At the time of writing it only supports amd64 processors and does not support LVM or RAID or other more[/FONT]
[FONT=serif]sophisticated storage options, nor does it support reusing existing partitions on the disks of the system you are[/FONT]
[FONT=serif]installing. It also requires access to the Ubuntu archive, possibly via a proxy. The previous, debian-installer[/FONT]
[FONT=serif]based, installer is still available if these restrictions mean you can't use the live server installer.[/FONT]

See Section 1.1 System Requirements.

[https://help.ubuntu.com/18.04/serverguide/serverguide.pdf](https://help.ubuntu.com/18.04/serverguide/serverguide.pdf)

It is possible to do an online upgrade from 16.04 LTS to 18.04 LTS. Then do an online upgrade to 20.04 LTS. Then do an online upgrade to 22.04 LTS. It is a lot of upgrading but it will work.

[https://ubuntu.com/server/docs/upgrade-introduction](https://ubuntu.com/server/docs/upgrade-introduction)

I think that the Debian installer server ISO image is called Legacy Server image. A Server image called daily-live will be using the new installer. I guess.

[https://cdimage.ubuntu.com/ubuntu-server/focal/daily/20200918/](https://cdimage.ubuntu.com/ubuntu-server/focal/daily/20200918/)

The Server images for 22.04 LTS seem to be using the daily-live images without any legacy images available.

Regards

---

### Post by MAFoElffen on 2023-02-11
Running the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") (ran from a LiveCD will tell us about the hardware and graphics capabilities... Please post the URL to where it uploads the report to a pastebin.

The Live installer, even though console based, uses psuedo vga graphics, please try using 'nomodeset' as a boot parameter in the Grub Menu...

---

### Post by guiverc on 2023-02-12
> **grahammechanical said:**
> 
The Server images for 22.04 LTS seem to be using the daily-live images without any legacy images available.


This maybe what you were looking for

[https://releases.ubuntu.com/22.04.1/](https://releases.ubuntu.com/22.04.1/) 

(ie. released ISO for 22.04.1, not daily of 22.04.2  .. though once installed & upgrades are applied; the result should be the same)

---

