---
title: "in Windows 8.1 64bit."
date: 2018-03-04
forum: Installation &amp; Upgrades
---

### Post by spi2 on 2018-03-04
in Windows 8.1 64bit. How to create persistent USB 64Gb (more 4Gb persistent), in what format FAT32, NTFS, etc. with what utility? Unetbootin?  Universal-USB-Installer-1.9.8.0? How can I install Skype?

---

### Post by oldfred on 2018-03-04
I do not know about persistence, I use full install to any flash drive 32Gb or more. 

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) 

      
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Do not know about Skype.

---

### Post by mastablasta on 2018-03-06
persistance will be limited anyway by the file system and persistence file size (arround 4 GB). you should probably use fat32 if you want it more universal. skype can be installed using the .deb file found on skype website.

as mentioned you might also consider full install. in that case do not install any additional drivers.

---

