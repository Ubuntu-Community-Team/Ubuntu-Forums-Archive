---
title: "Is there an easy way to install a .iso file to a usb/sdcard."
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2013-11-20
I ask because for example with the raspberry pi when configuring the OS all you need to do is DD over the raspberrypi.img file to the sdcard and you have a full install with root privileges but if you wanted to do something similar for a ubuntu.iso file first you need to create a bootable usb and point that to another usb/sdcard to install onto, so you can't just DD over the .iso file, is this correct or am I going about things the wrong way. Thanks

---

### Post by coffeecat on 2013-11-20
> **J_Me said:**
> so you can't just DD over the .iso file

Yes, you can. If you simply want to make a bootable USB/SD card for the live session and installer you can indeed dd the ISO.

```
sudo dd if=/path/to/ISO of=/dev/sdX
```

Obviously, change sdX to whatever the USB/SD card is showing up as: sdb, sdc, and so on.

If you want to create a conventional Ubuntu installation on a USB/SD card you do, of course, have to use the installer for that, and be careful where you install grub.

---

### Post by J_Me on 2013-11-20
What I meant was to have root privileges you need to do those steps, DDing over the .iso just create a live usb with persistence. [quote]you do, of course, have to use the installer for that[quote] What installer do you mean, the 'create live usb' thing that comes with ubuntu.

---

### Post by coffeecat on 2013-11-20
> **J_Me said:**
> What I meant was to have root privileges you need to do those steps,

What do you mean by having root privileges? If you make a conventional installation to a USB stick, the first created user is an administrative account which can elevate to root privileges in the terminal with sudo. If you create a live USB with dd or one the USB creator applications, the live session user has the username "ubuntu" with a UID of 999 and can also elevate to root with sudo in the terminal, and doesn't even need a password to do so.

> **J_Me said:**
>  DDing over the .iso just create a live usb with persistence.

Not with persistence. If you want persistence you'll need to use the Startup Disk Creator app.

---

### Post by J_Me on 2013-11-20
Yes what I mean by full install and root privileges is 'conventional' and when I say install I mean I would like to do a conventional install. I'm still confused about the 'installer', do you use an installer when you dd over the raspberrypi.img file to the sdcard. Thanks

---

### Post by oldfred on 2013-11-20
I think the Rasberry has only one hardware configuration, so it is possible to create a pre-installed image and just copy that image to be your system.

With PC, you have just about an unlimited number of combinations of hardware devices. The installer reviews all those devices as part of install and create the correct image file to boot your system. But it still is flexible enough to recognize most changes as it is booting. Also the software on the live installer is the compressed image, not the installed & configured as installed version has extracted and configured all your software and your User ID. That allows more software to be part of default ISO.

---

### Post by J_Me on 2013-11-20
Okay thanks alot I understand, it's to do with compressed files and different types of hardware configuration. Thanks again

---

