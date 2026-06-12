---
title: "plop bootmanager pcmcia usb live Ubuntu install problems"
date: 2011-01-29
forum: Installation &amp; Upgrades
---

### Post by ozooha on 2011-01-29
I run plop bootmanager - [http://www.plop.at/en/bootmanager.html#pcmcia](http://www.plop.at/en/bootmanager.html#pcmcia) to load live linux distros from the usb drive on the PCMCIA card. This is because grub2 doesn't yet support the pcmcia drivers and I wanted to make use of my old laptop.
I run the instruction on how one should install ubuntu on a usb stick from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download).
The process goes through when I see the live CD screen where it lets me try Ubuntu without installing. The splash screen comes up and all and remains there for sometime but after that it stops and then I get this error:
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter "help" for a list of built-in commands.

(initramfs) /scripts/casper-premount/20iso scan: line 46: can't open /dev/sr0: No medium found

Its trying to search for my cdrom drive when it shouldn't as I have it on usb drive!!!!!!!
Any experts out there have any suggestions/help/pointers etc.
Thank you for your time and attention.
OZooHA

---

### Post by ozooha on 2011-02-06
So I finally solved this problem. Here are the steps:
1)Install into grub2 the plop bootmanager - [http://www.plop.at/en/bootmanager.html#pcmcia](http://www.plop.at/en/bootmanager.html#pcmcia) to load live linux distros from the usb drive on the PCMCIA card
2) Use [unetbootin-windows-494]("http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/unetbootin-windows-494.exe/download") to create the USB drive for the ubuntu-10.10-alternate-i386.iso and NOT the live-cd iso.
3) Start the PC/notepad/laptop with the PCMCIA plugged (with the USB in it of course) into it. Once the grub comes up choose the option for loading the PCMCIA option. It will take you to the menu where you choose the USB drive and from there the normal installation process takes over.

---

