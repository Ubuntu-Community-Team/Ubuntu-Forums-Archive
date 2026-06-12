---
title: "USB installer boots to black screen on HP EliteBook 8440p"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by cyberiad on 2011-01-05
Hi all,

It's my first time trying to install Ubuntu. My problem is that booting from USB stick or trying to run "install to drive" both result in a black screen. Here are my specs:

HP EliteBook 8440p
Intel Core i5 M520 @ 2.40 GHz
NVIDIA NVS 3100M

Ubuntu 10.10 64-bit deployed to USB stick using Universal USB Installer 1.8.2.2.

Searching around seems the problem is the way Nvidia graphics card is handled. I found a recommendation to set 'nosetmode' option, but found no easy way to do this on the current USB boot menu.

Currently tried pressing TAB on the boot menu option and adding '--nosetmode' to command line, but result is the same.

Does anyone have any suggestion about what I should try next?

Thanks in advance.

---

### Post by cyberiad on 2011-01-05
An update. It seems that I can boot Ubuntu from the USB stick by using '--nosetmode' after all. However, for some reason this does not work for the "Install to Drive" option (sometimes it flashes colors like crazy on the screen).

Is it possible to do the install from a USB booted system?

---

### Post by cyberiad on 2011-01-05
Ok, managed to install Ubuntu with "--nosetmode".
Apparently in my current hardware setup, setting 'nosetmode' will work non-deterministically. Sometimes it boots correctly, sometimes not.

In the end I managed to install it. Thanks anyway :)

---

### Post by jaythedogg on 2011-01-05
> **cyberiad said:**
> Ok, managed to install Ubuntu with "--nosetmode".
Apparently in my current hardware setup, setting 'nosetmode' will work non-deterministically. Sometimes it boots correctly, sometimes not.

In the end I managed to install it. Thanks anyway :)

Kinda a newbie myself here, but I think it is "nomodeset", I may be wrong, but I think the "nosetmode" command is non-existent & would thus be ignored.

If you have trouble in the future, please try nomodeset instead.

---

