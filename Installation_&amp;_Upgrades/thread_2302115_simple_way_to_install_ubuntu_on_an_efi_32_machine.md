---
title: "simple way to install ubuntu on an efi 32 machine?"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by christopher-acosta-af on 2015-11-07
i was looking online for a way to install ubuntu on an efi 32 machine. all instructions seem pretty hard and while im not one for complaining about difficuly i am faced with doing this  procedure for multiple machines and this seems daunting. i work with a non-profit that wishes to implement ubuntu on several cheap efi 32 machines. are there any streamlined or automatic setup steps that doesn't require building grub on every machine?

---

### Post by grahammechanical on 2015-11-07
Your right it does seem complicated. It is made worse because the tutorials are related to a specific machine which is fine if it is the same as your hardware. But not so fine if you own different hardware.

The simplest method I have found is to install Ubuntu but not to restart and then from a live session install grib-efi-ia32-bin. It is at the bottom of this tutorial

[https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/](https://sturmflut.github.io/linux/ubuntu/2015/02/04/installing-ubuntu-on-baytrail-tablets-version-2/)

> [h=3][SIZE=2]The probably much better way (only available on Ubuntu 15.04) [/SIZE]Open a terminal and install the grub-efi-ia32-bin package:[/h]```
sudo apt-get install grub-efi-ia32-bin
```

Update the grub config

```
sudo update-grub
```

This is from 15.04 onwards. I can confirm that grub-efi-ia32-bin is in the 15.10 archives.

Regards.

---

### Post by mörgæs on 2015-11-08
When you search for guides then only read the 15.10 ones. What you have read for older releases might scare people for no reason.

A lot of work has been put into making 15.10 more straightforward to deal with on 32 bit EFI.

Besides, since 32 bit EFI often indicates weak hardware you could consider X/Lubuntu.

---

