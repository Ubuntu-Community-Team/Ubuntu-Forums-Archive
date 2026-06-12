---
title: "Install from usb hard drive"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by jmore9 on 2010-08-01
Hello !

I have been searching for a way to install ubuntu from an ISO image on a fat32 partition on an usb hard drive.  Have only found ways to install to a usb hard drive, not from.

When i did this with fedora the installer gave an choice of where to install from ( don't know if they still do ).

Thanks in advance for any help

---

### Post by snowpine on 2010-08-01
You can use the USB Startup Creator or Unetbootin to prepare a bootable Ubuntu USB drive.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by jmore9 on 2010-08-01
I have looked at those but they only work for usb flash drives, not hard drives.   I need a way of getting the installer to install from an ISO on an FAT32 partition.

---

### Post by snowpine on 2010-08-01
> **jmore9 said:**
> I have looked at those but they only work for usb flash drives, not hard drives.

Are you sure about that? It seems to me a USB drive is a USB drive is a USB drive, whether it's 1gb or 500gb.

But I have not tested it personally so there you go. :)

Is there a reason why you don't just buy an inexpensive thumb drive or blank CD?

---

### Post by jmore9 on 2010-08-01
I tried the usb flash ones and they always gave me errors on not finding a flash drive. did this 3 times gave up.

I am digging out the fedora 5 cd i made and see what is different from the new ones and maybe just use fedora seeming as the usb flash thingy doesn't work for me.

I am using a 40 gig WD hard drive not a flash drive.

---

### Post by snowpine on 2010-08-01
Fedora is a nice distro (I prefer it to Ubuntu personally) but you really should be using Fedora 13. Support for Fedora 5 ended a looooong time ago. ;)

---

### Post by oldfred on 2010-08-01
You can directly boot an ISO from grub2 on any partition, but of course cannot reinstall over the same partition.

[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO](http://ubuntuforums.org/showthread.php?t=1535864&highlight=ISO)

---

