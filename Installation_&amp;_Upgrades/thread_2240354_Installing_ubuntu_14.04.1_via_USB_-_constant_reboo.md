---
title: "Installing ubuntu 14.04.1 via USB - constant reboot loop."
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by James_Gibson on 2014-08-19
I am trying  to install Ubuntu 14.04.1 LTS via USB.

So far, I have created a bootable USB using pendrive and the default 64bit download on the Ubuntu desktop website.

When I boot from the USB, it shows me a purple screen for a few seconds (giving me the option to edit the install options) and then just reboots. This cycle continues.

Could anybody help me?

*Windows 8 is currently installed on my system, but I want to replace windows 8 with Ubuntu.

---

### Post by ubfan1 on 2014-08-19
"Purple screen"?  Thats the grub-pc, not for UEFI machines.  Are you trying this in compatibility mode?  Read about UEFI, then decide what you want to do -- Ubuntu should install just fine on a UEFI machine, fixing the bootloaders is a machine specific issue, with some harder than others:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

---

