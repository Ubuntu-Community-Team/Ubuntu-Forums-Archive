---
title: "hi everyone! looking to make a bootable USB drive"
date: 2018-09-25
forum: Installation &amp; Upgrades
---

### Post by sususudio on 2018-09-25
I installed UBUNTU as my main OS over a win 10 computer. I used rufus to create the bootable ISO USB.
Is there any similar function to rufus on ubuntu to create bootable USB drives?

---

### Post by oldfred on 2018-09-25
Ubuntu suggests Start up disk creator.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)

Many prefer mkusb:
       [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Bit more advanced, some of us just install grub and directly boot ISO with loopmount.

 [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) 

I now typically have ISO on either or both SSD & HDD. I then can install to either drive or to any external drive directly. My USB flash drives mostly have full installs, even if for data.

And if a newer UEFI system, you do not need an installer.
       
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formatted flash drive partition & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by C.S.Cameron on 2018-09-26
+1 mkusb.
It makes a boot partition, a read only OS partition a ext2 persistence partition and a Windows/Linux compatible NTFS data partition.

SDC only uses a little space on the flash drive but makes the rest of the drive useless.

---

