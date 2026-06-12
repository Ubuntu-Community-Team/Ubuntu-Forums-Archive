---
title: "[SOLVED] Ubuntu Flash Drive install - Grub error 22"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by Separ on 2008-06-13
I followed a guide on pendrivelinux.com to install ubuntu to a flash drive as a live version which saves your settings from inside an existing ubuntu install but whenever I try to boot from my USB drive, it shows
```
Grub stage 1.5

GRUB Loading...Please Wait.
Error 22

```

Is there any solution to this? I have set my BIOS to boot from USB first, CD/DVD Drive second, Hard drive third and Network fourth.

---

### Post by dstew on 2008-06-13
Can you provide the link to the tutorial you were following when you installed? There are a variety of ways to install Ubuntu to a pendrive.

In general, the error you are getting means that grub is mis-installed on the boot device.

---

### Post by Separ on 2008-06-13
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401)

I wiped the drive again and tried to install pendrivelinux on it and it gave me the same grub error.

---

### Post by meierfra. on 2008-06-13
It seems that the MBR of your flash drive is corrupt. Try this

[http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/]("http://www.pendrivelinux.com/2007/03/07/install-a-new-mbr-to-your-usb-flash-device/")

---

