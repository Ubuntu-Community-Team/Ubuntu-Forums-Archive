---
title: "Ubuntu installs fine, dies at boot"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by Ghaleon on 2005-07-11
I installed Ubuntu with the default install, everything seemed ok, even the post-install config went fine. After that, I just get a screen with an underscore on it. Nothing else happens. Any ideas?

600Mhz Pentium Celeron
320MB RAM
Nvidia Geforce4 MX420

Edit: Installing under VMWare works just fine, but I'd like it as a primary OS...

---

### Post by varunus on 2005-07-12
Sounds like a video issue.  Boot into recovery mode from the GRUB boot menu, and enter the following:

```
nano /etc/X11/xorg.conf
```

Scroll down to the Device section and change the Driver line to:

```
Driver  "vesa"
```

Then try rebooting.  Did this work?  If it did, you need to install the proprietary nvidia driver.

Good luck.

---

### Post by Ghaleon on 2005-07-12
Thanks a lot. I'll try that on my next install. I just need to re-backup first.

---

### Post by sisya on 2005-07-12
set it to "vesa"...

ya done that....

it did go further ...but it still gave me

"i could not start your xserver(graphical interface) coz its not setup properly......"


where do i go from here??

---

### Post by Ghost Freeman on 2005-07-18
[QUOTE=sisya]set it to "vesa"...

ya done that....

it did go further ...but it still gave me

"i could not start your xserver(graphical interface) coz its not setup properly......"


where do i go from here??[/QUOTE]


Yeah, that's where I am at right now (Celeron 600MHz, Voodoo 3, 256MB SDRAM). Although my GDM crapped out in the middle of an install(!) was able to get this screen albeit distorted with vesa.

---

