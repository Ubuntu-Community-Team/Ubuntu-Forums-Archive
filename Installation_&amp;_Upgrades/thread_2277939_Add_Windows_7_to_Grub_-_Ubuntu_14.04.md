---
title: "Add Windows 7 to Grub - Ubuntu 14.04"
date: 2015-05-12
forum: Installation &amp; Upgrades
---

### Post by seba7 on 2015-05-12
[http://paste.ubuntu.com/11068580/](http://paste.ubuntu.com/11068580/), if someone could help?


Seb

---

### Post by tim105 on 2015-05-12
Run the following command:

> sudo update-grub

That will reload Grub and any partitions with an existing OS will be added to the boot menu.

---

### Post by yancek on 2015-05-12
You installed Ubuntu using UEFI and have the proper files in the proper location.  You don't indicate which Installation Type option you used but whichever one it was, you've overwritten your windows partition.  The only sign of windows are the efi boot files on the first partition.  Re-install windows looks like the only option as you don't seem to have a Recovery partition.

---

### Post by seba7 on 2015-05-12
Thank you yancek, I'll try re-install windows, and we will see

---

### Post by seba7 on 2015-05-15
Is there a way to install win7 from usb, since my dvd rom not working?

---

### Post by seba7 on 2015-05-15
I'll try winusb program

---

### Post by Vladlenin5000 on 2015-05-15
If you have access to a Windows machine you can use the Microsoft tool for that and an ISO, of course. Actually, if you intend to install Windows 7 in UEFI mode, I think you must use an USB written with that.

WinUSB seems to be no longer developed so I would advise against using it. You may have problems trying to install old software in newer releases and it most certainly wouldn't support UEFI.

---

