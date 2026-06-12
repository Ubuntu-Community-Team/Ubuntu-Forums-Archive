---
title: "BOOTMGR is missing"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by walesmd on 2010-01-18
I am attempting to install Ubuntu Netbook Remix (I even tried Ubuntu Desktop) off of a USB drive. I use unetbootbin to prep the drive, my BIOS is configured to boot off the USB Hard Drive, after booting up the computer I get a message that reads "BOOTMGR is missing, Press Ctrl+Alt+Del to restart" This laptop is currently running Windows 7 which, after removing the USB Drive, boots up fine.

I've seen other posts on this but they all refer to dual-booting and modifying grub configuration files. I'm not even to that point yet (and don't even want to dual boot, to be honest) - I'm just trying to get onto the "LiveCD" so I can format and install.

Any ideas?

---

### Post by walesmd on 2010-01-19
Guess I'll try burning it to a CD tonight...

---

### Post by darkod on 2010-01-19
unetbootin messed something up. Or there is some previous mess involving the boot sector of the usb stick. My suggestion:

1. Format the stick again as FAT32, to make sure you get rid of everything.
2. Use unetbootin again to copy the UNR image to the stick. IGNORE the message to reboot after it finishes, just close unetbootin.
3. To get rid of the unetbootin menu, open the stick and do:

-in the root folder rename syslinux.cfg to syslinux.old
-in the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
-go back and rename the whole folder isolinux to syslinux

This procedure will make available the standard ubuntu menu which gives you options to Try Ubuntu, Install Ubuntu, etc. Otherwise, the problem with unetbootin is that it creates its own menu with one entry called 'default' which starts the install process right away, as if you selected Install Ubuntu. To my knowledge, you will not have option to Try Ubuntu if you don't do the above procedure.

---

