---
title: "Can't get Unletbootin boot drive to work?"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by demonic_crow on 2010-01-31
I tried making an os usb boot drive using the unetbootin in ubuntu and it just stay at a gray screen.  It says press Tab to edit option and then there another thing that mention Automatic boot in "" seconds which just keep counting over from 10.  Anyone know what might be causing this issue and how I might be able to solve this, thanks.

---

### Post by darkod on 2010-01-31
I use unetbootin mainly on windows. If you already have working ubuntu the best way is to format the stick as FAT32 (in ubuntu or windows) and then use the USB Startup Disc creator in System-Administration.
That's a much better way.
If you still insist on unetbootin, I found out that it replaces the ubuntu menu with its own menu and that sucks. To make the ubuntu menu available you could open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the standard main ubuntu menu.

---

### Post by C.S.Cameron on 2010-01-31
If it still dosn't work with usb-creator, check the MD5Sum of the iso to make sure there are no errors.

---

