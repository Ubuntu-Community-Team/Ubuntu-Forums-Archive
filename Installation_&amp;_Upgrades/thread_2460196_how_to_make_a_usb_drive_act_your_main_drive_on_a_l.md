---
title: "how to make a usb drive act your main drive on a laptop"
date: 2021-04-04
forum: Installation &amp; Upgrades
---

### Post by tekno62 on 2021-04-04
I can boot from the usb drive but ubuntu wants to install on my main drive. I want to install it on a usb drive with all the correct drivers and have the usb drive act as my main drive.

---

### Post by CelticWarrior on 2021-04-04
So tou need to select the other USB drive for the installation. You can't install to the same.

---

### Post by grahammechanical on 2021-04-04
I do not understand what you are trying to do. Is it

a) Burn a Ubuntu iso image to a USB memory stick and then run a Ubuntu live session?

b) From a Ubuntu live session install Ubuntu to a USB memory stick?

To burn a Ubuntu iso image to a USB memory stick to run a live session from the USB stick with the option of installing Ubuntu to a hard drive follow these instructions:

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

To use Ubuntu from a USB memory stick as a main OS, we install Ubuntu with persistence. This creates partitions on the USB stick in which applications and data can be stored and not be lost when we shutdown Ubuntu. Which is what happens with a Ubuntu live session. To install Ubuntu on a USB memory stick with persistence follow this guide:

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

If we have 2 USB ports and 2 USB memory sticks it is possible to use a Ubuntu live session on one USB stick to install Ubuntu with persistence on the other USB stick. It is possible but we have to be careful we do not install Ubuntu on the hard drive by accident. I prefer to do both the burning of the iso image to USB stick and the install with persistence to a USB stick from Ubuntu installed on a hard drive with an iso image downloaded to the hard drive.

Regards

---

### Post by tekno62 on 2021-04-04
this is what I want to do

> **grahammechanical said:**
> I do not understand what you are trying to do. Is it

[https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

If we have 2 USB ports and 2 USB memory sticks it is possible to use a Ubuntu live session on one USB stick to install Ubuntu with persistence on the other USB stick. It is possible but we have to be careful we do not install Ubuntu on the hard drive by accident. I prefer to do both the burning of the iso image to USB stick and the install with persistence to a USB stick from Ubuntu installed on a hard drive with an iso image downloaded to the hard drive.

Regards


thanks

---

### Post by C.S.Cameron on 2021-04-04
For a simple method to fully install to USB see: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)

For a more traditional method see: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

enerally when you Full  install to external drive you want ot to be able to boot on both BIOS and UEFI computers.

---

### Post by ActionParsnip on 2021-04-05
The installer doesn't care how the storage is connected. It's a disk. Just partition as you would on an internal drive. It doesn't make any difference. Just remember to put GRUB on destination USB when asked during installation and you have a winner

---

### Post by tea for one on 2021-04-05
Please refer to this bug report to be fully aware of a potential hazard.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

