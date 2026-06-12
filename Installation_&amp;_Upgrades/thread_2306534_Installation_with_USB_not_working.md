---
title: "Installation with USB not working"
date: 2015-12-16
forum: Installation &amp; Upgrades
---

### Post by Amitoj_Kaur on 2015-12-16
Hello,

I have been trying to install Ubuntu 14.04 LTS on my Dell Inspiron 15R Laptop (64 bit) for the past week and I'm not able to.

I already have Windows 10 on my system and I'm trying to do a dual boot. I used UNETBootIn to convert it to a USB format.

I checked my settings and it is not a UEFI but a normal boot.

It gives me a ACPI PCC Probe Failed but I am not able to turn off acpi. The terminal cannot get gksudo for updating the grub file from the terminal.

Also when selecting 'e' from GRUB to turn it off from the Boot Loader I do not get any option to do so.

What should I do?

---

### Post by deepakdeshp on 2015-12-17
Have you been able to install Ubuntu on the disk drive?

If not then:-
You should be able to create a bootable usb from the Ubuntu iso image and able to boot from the USB. 
You may have to disable secure booting 
[http://askubuntu.com/questions/236787/install-ubuntu-next-to-windows-8-uefi-dual-boot](http://askubuntu.com/questions/236787/install-ubuntu-next-to-windows-8-uefi-dual-boot)

If you have already installed:-

[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

