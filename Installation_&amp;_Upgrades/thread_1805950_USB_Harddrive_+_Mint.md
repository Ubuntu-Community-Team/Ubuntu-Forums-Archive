---
title: "USB Harddrive + Mint?"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by Howy on 2011-07-16
So, I've got too much space on my HDDs, and one of them is portable. So I want to put Mint on one of the partitions. (It's an ext4 partition at the moment.)
So far, I've tried installing with the regular installer from a liveDVD within VirtualBox, but it freezes. I've extracted the squashfs to the harddrive, chrooted into it, install extlinux, but it fails to boot. (I did get into syslinux, but it couldn't boot because it didn't find the configuration. It's still possible to do something further with it, though.)
I've also tried USB creator, but it didn't work.

Also, I'd like to install from within my Ubuntu installation. I don't have any DVDs at hand right now. (The one I tried to use was rendered unusable due to a failed writing... I tried making it re-recordable so that I could use it again...)

Any advice on installing it to this drive? It would be handy to carry around, because I'm the only Linux user in the house, and I use ext3 partitions for my stuff. (They're so much faster than FAT and NTFS. Not worth it to switch. ;) )

---

### Post by ManualSparrow on 2011-07-16
I am just about to do the same thing, but with OpenSUSE. My plan is to make an installation media (burn the .iso to a CD) and then do a standard install specifying the extra partition as the / mount point and putting the external drive as the target for GRUB. There is some option called 'uuid' that I am looking into that makes sure that GRUB can find your extra install no matter what hard drive number (hd1, hd0, etc) the BIOS gives the drive. Of course I haven't done it yet, so not sure if it going to work out or not.

Hopefully that is helpful.

EDIT: Sorry, I forgot you had no DVDs at hand.

---

### Post by cipherboy_loc on 2011-07-16
A tutorial I used (though I used GParted rather than FDISK for partitioning and set the partition type to ext4 rather than FAT32).:

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

I suspect the general steps are the same for Mint, but OpenSUSE might have a different location for the kernel and initrd.


Cipherboy

---

### Post by Howy on 2011-07-17
It doesn't work with what they suggest at PenDriveLinux. It doesn't provide data persistence.
However, I've found out that USB Creator does make a bootable device with MBR and GRUB, but it doesn't find the kernel. I end up in the syslinux prompt, but I can't get any further. The kernel and the initrd are existing, but it doesn't find it.
Should I use grub-install to fix this?
Currently, it provides a loopback.cfg file, and also a persistive casper-rw file. Sadly, it just won't boot the kernel.
Is there anything I can do about this?

Or... It says it can't find vesamenu.c32... But that one is also there.
I used USB Creator completely fine once before. (With persistent data storage.)

---

