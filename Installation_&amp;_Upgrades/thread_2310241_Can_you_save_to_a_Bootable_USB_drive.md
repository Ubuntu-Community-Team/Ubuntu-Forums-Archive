---
title: "Can you save to a Bootable USB drive?"
date: 2016-01-17
forum: Installation &amp; Upgrades
---

### Post by rcknrolfender79 on 2016-01-17
Hey guys/gals, I'm new to the forum and never used Ubuntu before. I've been wanting to check it out. I'm wanting to make a Bootable USB drive. When this is done are files downloaded or installed from the USB  saved on the USB? For instance if I install a program does that program and all it's data get stored on the USB with Ubuntu or would I have to bring another HEr into it? Also for arguments sake lets say I have a 32GB USB drive... Should I partition that entire drive for the Ubuntu install? Would that give me more space for installs and downloads in Ubuntu? Or should I only partition the space needed for the OS itself? Say 1.5 to 2Gb? Trying to get everything figured out before I do this. I don't really want to have a whole bunch of mixxed up files for windows and ubuntu on my PC lol.

---

### Post by rcknrolfender79 on 2016-01-17
HDD not HEr.... Autocorrect lol

---

### Post by oldfred on 2016-01-17
Depends on how you install. The installer can have extra space. But you cannot update installer, but can save some data to a persistent install. If you have a 32GB flash drive then a full install may be better and just use the entire 29 or so usable space as / (root). Then you can do full updates. 
 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

 [URL="http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal"]http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal
[/URL]
 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Full install to a flash drive is like any other install to a second drive. Whether newer UEFI or older BIOS boot. And if USB3 flash drive in USB3 port works reasonably fast if you modify a few settings to reduce writes.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
Howto help USB boot drives - sudodus
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)[URL="http://askubuntu.com/questions/295701/what-would-be-the-differences-between-a-persistent-usb-live-session-and-a-instal"]
[/URL]

---

### Post by yancek on 2016-01-17
With a 32GB flash drive, creating two partitions, one for the Ubuntu install and one for data would probably be the simplest.  If you are planning to share it with windows, you will need to use an ntfs or FAT32 filesystem as windows is not capable of reading a Linux filesystem.  Additionally, windows will only see the first partition on a flash drive so you would need your data partition there.

If you used an actual external hard drive, using the first as ntfs would not be necessary but given the size of the drive I'm assuming it is a flash drive?

---

### Post by rcknrolfender79 on 2016-01-19
> **yancek said:**
> With a 32GB flash drive, creating two partitions, one for the Ubuntu install and one for data would probably be the simplest.  If you are planning to share it with windows, you will need to use an ntfs or FAT32 filesystem as windows is not capable of reading a Linux filesystem.  Additionally, windows will only see the first partition on a flash drive so you would need your data partition there.

If you used an actual external hard drive, using the first as ntfs would not be necessary but given the size of the drive I'm assuming it is a flash drive?

Yeah its a flash/usb thumb drive.. whatever you want to call it.

---

