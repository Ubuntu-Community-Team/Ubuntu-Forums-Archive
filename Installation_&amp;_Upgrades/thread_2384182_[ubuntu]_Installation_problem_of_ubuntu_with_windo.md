---
title: "[ubuntu] Installation problem of ubuntu with windows 10"
date: 2018-02-03
forum: Installation &amp; Upgrades
---

### Post by netsho on 2018-02-03
[LEFT][COLOR=#000000][FONT=Ubuntubeta][SIZE=2]Hello,

I have a Lenovo i7 second generation with 750GB o hard drive.  I've gone in Windows and created a separate partition of 100GB (which is sufficient for me).  I've installed Ubuntu 17.10.1 on USB and boot to it (created the usb boot with linux USB livecreator).  I start the installation and I follow it until i reach where to install Ubuntu. Normally, i should have "install Ubuntu alongside windows10", but i only have "erase Windows and install linux". I select Something else, but i can't click on the "+" button on the free space in order to change options. I have also changed the partitions with Gpart and Nothing. I also tried to switch off Fast launch but i still can't get the installation along with Windows.
Also one more thing, when i try to install, it tells me if i really want to install on the UEFI mode. I select no because Windows is installed on legacy mode and i can't risk to loose it.

Note : i already installed the linux on my first computer with no problem, i had the "install alongside Windows" option. But i can't make it on the second computer.

Thank you in advance[/SIZE]
[/FONT][/COLOR][/LEFT]

---

### Post by oldfred on 2018-02-03
Un-Bolded your post.

IF you have BIOS/MBR configuration, have you  used all 4 primary partitions?
Or by creating partitions with Windows did it convert from Basic to Dynamic which is proprietary to Windows and does not work with Linux?

Post this from live installer:
sudo parted -l
sudo fdisk -lu

How you boot install media, UEFI or BIOS is then how it installs. And then whichever screen you see will confirm how you booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

