---
title: "Installed gutsy ok but no option to boot from grub"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by desertboy on 2007-11-07
I have gutsy already installed, I wanted a 2nd copy installed on my 500gig sata drive, I've installed it alright but I thought gutsy installation program would add it to grub which it hasn't anyone help in getting it to boot.


I have gutsy on drive A
I installed gutsy on drive B (Used to be Vista)
Drive B is set as boot drive, grub lives on drive B

Drive A gutsy boots fine, drive B gutsy I have no option to boot in grub.

---

### Post by dabl on 2007-11-07
Assuming you left the first hard drive connected, the second installation should have added the first Gutsy OS to the new boot menu.  But I guess it didn't, so you will have to edit the /boot/grub/menu.lst file to add the drive and kernel that are missing from your boot menu.  Here is a lot of guidance on the subject:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by desertboy on 2007-11-07
I found the menu.lst which the install to drive B had written added the entry to my original menu.lst (On drive A) now it says failure to mount disk.

---

### Post by bulldog on 2007-11-07
Copy the output of ```
sudo fdisk -l
``` to the forum and a copy of the menu.lst as well.

---

### Post by desertboy on 2007-11-08
sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x203e9480

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xafa8afa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78be03ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60045   482311431   83  Linux
/dev/sdc2           60046       60801     6072570    5  Extended
/dev/sdc5           60046       60801     6072538+  82  Linux swap / Solaris


menu.lst


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=466e842a-1ed1-4f40-8061-0b6f28292e9b ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8418bd87-6e07-470d-aa45-7385fb9ced9f ro quiet splash irqpoll
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by bulldog on 2007-11-08
Yes,well,I see three hdd's listed instead of two?

Edit:
is that all what's listed in menu.lst?
Which entry is your first ubuntu on sda?

---

### Post by desertboy on 2007-11-08
the top one hd1 (sda) is the original booting gutsy, sdc is the 500gig whith the installed but unbootable copy of gutsy. sdb is a 300gig NTFS used solely for storage and will be moved over to native as soon as the dual booting is out the way.

I just cut out the dafult options bit at the top the only thing I've put in there is irqpoll which I need to boot Ubuntu


I'm going to try changing my menu.lst to hd3,0 in the 2nd boot option (The one that doesn't boot)

---

### Post by bulldog on 2007-11-08
A smarter way is at boot time.
Select the line you want to boot and hit the  e [edit] change it into another hdd and hit the b and see what happens.
when you have a go note it to set the menu.lst proper.
But I think there should be more options in your menu.lst.
Three for each distro as a minimum.

---

### Post by desertboy on 2007-11-08
Solved I need the boot device set as hd0,0 then it works, thanks for helping. I now have 2 working copies of Gutsy on my machine I finally feel I can delete the final NTFS and say good riddance to windows for good.

---

