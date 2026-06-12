---
title: "Writting ISO to USB pevents using unused space"
date: 2018-08-11
forum: Installation &amp; Upgrades
---

### Post by sushi-addiction13 on 2018-08-11
every time I write a buntu iso to a USB, I can't do anything with the unused space.

I want to use it. On a 16GB flash *buntu takes up 2GB, the 14GB is wasted.


I've tried creating extra partitions but nothing works.

---

### Post by kc1di on 2018-08-12
Hi,
If you want the drive  to have persistence that is be able to store files while using the live usb version of ubuntu. [this page]("https://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/") will be of help.

---

### Post by yancek on 2018-08-12
That is certainly possible but it depends on several factors.  You can, as suggested above, create a persistent system with some software.  If you want a persistence partition that large it will need to have a Linux filesystem on it.

You can install Grub to a separate boot partition and then put your 'live' Linux iso on another partition and boot it.  You would need to modify your grub.cfg menuentry for each new system to boot the iso.  Lots of tutorials and examples online of how to do this.

You can use GParted on another LInux sytsem to shrink the space on which you have written the system and create another partition.  You should then be able to use it to put data on.  If you want to boot the 'Live' system and put data on the second partition, you will have to manually create a mount point each time and manually mount it each time.  That's the way it's designed.  You could just do an actual install to the usb also although 16GB is a little small.

---

### Post by oldfred on 2018-08-12
If 16GB or larger, I prefer to do a full install, and add some repair tools like gparted & Boot-Repair. But also then add ISO and grub loopmount directly boot ISO. I use about 8GB for install, but it is not a working install where I add lots of other applications. 

But full install to any external drive is different if UEFI or BIOS.

If an UEFI system, you can just have a FAT32 partition for the live installer.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by C.S.Cameron on 2018-08-12
Mkusb makes a FAT32 Boot partition and boots UEFI or BIOS. 

It makes a read only ISO9660 partition for the OS.

It can make an ext4 casper-rw persistence partition not limited to 4GB.

And it also can make a NTFS data partition usable by Linux and Windows, as large as there is room on the USB.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

You can install mkusb on your Live drive with the unusable space.

---

### Post by sushi-addiction13 on 2018-08-12
- gparted reports errors every time. It always has. The is no way to make another partition after writing the iso to usb.
- Mkusb has the same problem BUT can get around that with persistence
> **mkusb**  will 'use the whole device', actually only the head end (size of the  iso file), but the rest of the device is not available.
> And when you have started along the persistent path, some warnings may  pop up and finally you are prompted to select the percentage of the  remaining drive space for persistence. The rest of the drive space is  used for storage compatible with Windows.
- persistence, It's takes time but may be the best option with [B]mkusb.
[/B]- Full install. No messing around with partitions. Needs to load live image to install on another USB. Soo much Extra time. Probably the most failsafe option.
- Grub, Sorry, I'd rather have teeth pulled**. **No UEFI on my system too**

I'm after a live image that's like the using a dvd BUT with the extra space available if it's quick and easy

I'll play around with mkusb, If not full install.

[COLOR=#0000cd]The  whole problem is buntu iso can't be put on usb and still be able to have  extra space usable. It is a rather large negative point IMO.[/COLOR]

** If I had UEFI I'd try
> Extracting the content of an Ubuntu 64-bit desktop ISO file to a  partition with a FAT32 file system and a boot flag will do the job: to  create a live drive, that boots only in UEFI mode. It is called 'Copy  files from the ISO method' here (in the accepted answer).
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by sushi-addiction13 on 2018-08-13
what I really want to do is write a simple script but I think I'll wait until I buy a new system. My current dooesn't have uefi

I'll use "file-roller" or whatever to extract iso to usb and the "parted" to set "boot" flag

... just remembered. Virtualbox does uefi. I think I'll test this out.

dd if=/dev/zero of=output.img bs=1M count=1024
mkfs.ext4 output.img
[http://www.upubuntu.com/2012/03/how-to-create-img-file-and-change-its.html](http://www.upubuntu.com/2012/03/how-to-create-img-file-and-change-its.html)

parted /dev/sdX set 1 boot on
[https://www.linuxquestions.org/questions/linux-newbie-8/change-boot-flag-in-terminal-905477/](https://www.linuxquestions.org/questions/linux-newbie-8/change-boot-flag-in-terminal-905477/)

parted -l
or
fdisk -l

---

