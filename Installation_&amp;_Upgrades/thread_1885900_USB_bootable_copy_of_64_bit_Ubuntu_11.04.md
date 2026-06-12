---
title: "USB bootable copy of 64 bit Ubuntu 11.04?"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by Worlds Tallest Engineer on 2011-11-24
Where can I get a USB bootable copy of 64 bit Ubuntu 11.04?

I just installed 11.10 on my computer, with MS7 on the other part of my hard drive.  I've backed up all of my files on the MicroSoft side.  Now I want reinstall 11.04 over 11.10, but I can't find a copy. 

PS My CD drive is broken.

---

### Post by darkod on 2011-11-24
The ISO images are the same, doesn't matter if you will create bootable cd or bootable usb with it.
If you question is about finding the 11.04 images, they are here (select the one you need from all the links):
[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

---

### Post by WasMeHere on 2011-11-24
Some of this (but not everything) may be relevant for you:

This is how I repartition and format my USB drives to make them easily bootable:

0. Backup private files (if you have on the USB drive).

1. Use ***gparted***, which can be run either from a live environment or from the installed Ubuntu. Run ```
sudo apt-get install gparted
``` if necessary.

2. Delete existing partition(s) and create at least one new partition

3. Make a FAT32 file system in the first partition

4. Add the BOOT flag and the LBA flag

5. Add a descriptive label if you want (it helps identify the partition, but is not necessary) for example USB-1104
_____

Try if you find something useful for you in the following post!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11451221&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11451221&postcount=4")

and in the following internet links
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[[COLOR="RoyalBlue"]_http://www.bootdisk.com/pendrive.htm_[/COLOR]]("http://www.bootdisk.com/pendrive.htm")
[[COLOR="RoyalBlue"]_http://www.pendrivelinux.com/_[/COLOR]]("http://www.pendrivelinux.com/")
[[COLOR="RoyalBlue"]_http://unetbootin.sourceforge.net/_[/COLOR]]("http://unetbootin.sourceforge.net/")
[[COLOR="RoyalBlue"]_MultiSystem_[/COLOR]]("http://liveusb.info/dotclear/")

---

