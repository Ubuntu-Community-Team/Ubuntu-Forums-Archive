---
title: "Install Ubuntu feisty 7.04 from a usb drive"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by tapash on 2007-06-01
[SIZE="4"][COLOR="Red"][COLOR="DarkOrange"]***[FONT="Lucida Sans Unicode"]My computer has no CD/DVD drive, but i can boot from USB hard drive or USB drive. Can anyone please tell me how can i install Ubuntu Feisty from a usb drive. Please reply whether is it possible or not. Thank you[/FONT]***[/COLOR][/COLOR][/SIZE]

---

### Post by frozinfire on 2007-06-01
Yup, it's easy. From Windows XP:

Download [this]("ftp://ftp.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.36.tar.gz") and extract it.
Go into the program's mbr folder and copy mbr.bin to your empty flash drive.
Run cmd, cd to the program's win32 folder, and type "syslinux b:" (or whatever drive your stick is).
Extract Ubuntu's iso to the flash drive, so that the folders look like they would on a cd.
Move the contents of the isolinux folder to the main area.
Rename "isolinux.cfg" to "syslinux.cfg"

Let me know how it goes. :)

---

### Post by tapash on 2007-06-01
**[SIZE="6"]Thanks mate, i'll give a try and let you know[/SIZE]**:D

---

### Post by macmatt on 2007-06-03
> **frozinfire said:**
> Yup, it's easy. From Windows XP:

Download [this]("ftp://ftp.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.36.tar.gz") and extract it.
Go into the program's mbr folder and copy mbr.bin to your empty flash drive.
Run cmd, cd to the program's win32 folder, and type "syslinux b:" (or whatever drive your stick is).
Extract Ubuntu's iso to the flash drive, so that the folders look like they would on a cd.
Move the contents of the isolinux folder to the main area.
Rename "isolinux.cfg" to "syslinux.cfg"

Let me know how it goes. :)

Uhmmm THAT didn't work!. What do you mean by "the main area"?. Root of Flashdrive?. This failed, miserably!.

---

### Post by frozinfire on 2007-06-03
There's really no need to be rude. I successfully used this approach for three different Ubuntu versions, as well as other distros, but it's unfortunate if your attempt failed.

Yes, the root of the drive, outside of any folders.

---

### Post by tapash on 2007-06-21
[SIZE="5"]unfortunately Wasn't work[/SIZE]

---

