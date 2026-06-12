---
title: "Booting Ubuntu 16.04 from a pendrive with persistent storage"
date: 2018-01-31
forum: Installation &amp; Upgrades
---

### Post by loukitkhemka on 2018-01-31
I am trying to create a live ubuntu usb drive using etcher. The instructions I was following was from this page:
[https://www.lifewire.com/create-uefi-bootable-ubuntu-usb-drive-2202085](https://www.lifewire.com/create-uefi-bootable-ubuntu-usb-drive-2202085)

However, after the OS image was etched in the pendrive, I cannot create the casper-rw file because I am unable to view the pendrive in the disc list.

Upon checking in the disk management, I am only to see the unallocated space.

Please help me with any solution. Any other technique will also do.

---

### Post by sudodus on 2018-02-01
There is another tool, mkusb, that works in linux, and that can create a persistent live drive automatically, including a casper-rw partition. See the following links

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

[hr][/hr]
If you want to create a persistent live drive from Windows, you use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/compressed-image_2_USB-or-SD) to clone from an image file according to the following link,

[Compressed image file with a persistent live system](https://help.ubuntu.com/community/mkusb/persistent#Compressed_image_file_with_a_persistent_live_system)

---

### Post by C.S.Cameron on 2018-02-01
I always use mkusb for making a Persistent USB in Ubuntu, For making a Persistent USB in Windows I find UNetbootin easiest. Both tools work for BIOS and UEFI.
If the USB is over 16GB I use a Live USB to do a Full install to the drive. It is more stable than a Persistent install, is more secure, boots faster, uses space more efficiently and can be updated and upgraded.

---

