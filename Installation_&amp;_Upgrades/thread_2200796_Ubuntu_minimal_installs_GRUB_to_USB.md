---
title: "Ubuntu minimal installs GRUB to USB"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by Mantas_imknas on 2014-01-21
The installation goes fine, but when it comes to the GRUB installation, the installer tries to put it on the USB drive. For some reason, the usb drive is detected as /dev/sda and the HDD is at /dev/sdb.
I tried answering "no" to the "Install GRUB boot loader to the master boot record". It allows me to enter where GRUB should be installed, HOWEVER, when I start typing, what appears is garbage and not letters - some distorted symbols and that's all.

I have found a solution here: [http://superuser.com/questions/176050/ubuntu-server-installed-from-usb-putsgrub-on-theusb-drive-instead-of-the-hard](http://superuser.com/questions/176050/ubuntu-server-installed-from-usb-putsgrub-on-theusb-drive-instead-of-the-hard)

More precisely:

> 
[LIST=1]
[*]Start the installation from USB pen boot
[*]Select (country).archive.ubuntu.com
[*]After setting Clock remove USB pen
[*]Continue installation without USB
[*]GRUB gets installed automatically on the right disk
[/LIST]

However, I'm not sure whether this is the right way to do it. Is it okay to install it like this? The installation went fine after I followed those steps. Should I be worried?

---

### Post by ibjsb4 on 2014-01-21
If it boots, your good :)

---

