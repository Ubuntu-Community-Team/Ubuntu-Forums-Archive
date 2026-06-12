---
title: "USB Persistent with multiple partitions"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by cjpbob on 2008-11-28
I really enjoy the simplicity and speed of my persistent USB installation of Ubuntu 8.10, but my work requires me to keep my Windows build as my primary operating system.

My one gripe about using the USB ubuntu is that I can't figure out how to allocate only a portion of my 8GB drive to ubuntu. Ideally, I'd like to give it 4GB and keep the remaining 4GB(likely in a different partition) that can be accessed as file storage by both my windows OS and ubuntu.

Has anyone done this or at least know how? I'm new to this and the only experience I have with setting up ubuntu is from following instructions from places like pendrivelinux. If you have any help to offer, try to remember that I don't know much about this.

Thanks!

---

### Post by Mud.Knee.Havoc on 2008-11-28
If I understand you correctly, you should be able to specify the size of your Ubuntu partition when creating the persistent installation.

If you have an 8GB stick, tell it to use half of that, then the other half should be able to be formatted later on using gparted.  

EDIT: With gparted, you would create a FAT16 or FAT32 partition in the remaining (empty) half of the drive.  Warning! I haven't done this myself - I just went for the full 8GB.  But it should work just like any other drive, as far as I can see.

---

### Post by cjpbob on 2008-11-29
I redid my partitions and now am running the persistent version on a small 750MB partition and have a little over 3 allocated to casper.

I have the last half of my drive completely unallocated, but I can't figure out how to create a partition on it that is accessible in both Ubuntu and Windows. I can make a FAT16/32 partition with gparted, but I can't activate it from within Windows to assign it to a drive letter with the windows disk manager. 

When I activate the third partition on my thumbdrive with fdisk, it renders the thumbdrive unbootable and I have to use the live CD to fix it back.

What are we missing here?

---

### Post by AldenIsZen on 2009-01-03
I am looking for something similar, before I even tried to boot to USB this was my question. I read somewhere that you have to change the driver in Windows... but that will only work on the local PC where this is changed /me thinks.

---

### Post by cjpbob on 2009-01-03
I figured out how to do exactly what I was describing. Maybe that will help you figure out how to do whatever it is you're trying to do.

The trick is that while Ubuntu will recognize many partitions on a flash drive, Windows will only recognize and mount one; namely, the first one. So by partitioning my 8GB flash drive into three partitions this way and in this order:

P1 - 4GB FAT32
P2 - 750MB FAT16
P3 - 3.25GB EXT2

I can use the first partition to store data and files like a normal thumbdrive in either Ubuntu or Windows as well as use it to play media on some flashdrive-enabled game consoles and set-top DVD players. The second partition is flagged with the 'active' or 'boot' flag and can then be used to boot the slightly modified Live CD and the third partition rounds out the rest of the space on the drive and is used for the casper persistent stuff. Neither the 2nd or 3rd partitions are mountable from within Windows, which results in me essentially taking an 8GB thumbdrive for Windows and turning it into a 4GB thumbdrive for Windows which can also be used to boot a fairly featured and hearty build of ubuntu. The first partition of the thumbdrive is accessible for general-purpose file storage in both OSes, making it very easy to transfer files between them (without granting ubuntu access to the internal HD from which Windows boots.)

Hope this help.

---

### Post by AldenIsZen on 2009-01-03
> **cjpbob said:**
> ...The second partition is flagged with the 'active' or 'boot' flag and can then be used to boot the slightly modified Live CD and the third partition rounds out the rest of the space on the drive and is used for the casper persistent stuff. ...

 Genius, not sure why I didn't think to try that.. maybe to get others perspective and save time. I currently have the full blown install and will try that now and report back, as on the first couple of attempts the persistent install didn't boot.

 I would rather the full blown as I can update it, however the persistent seems to have advantages, such as better USB stick life. Others have not had luck it seems with updating the persistent.

---

### Post by AldenIsZen on 2009-01-03
It worked like a charm, sort of. The only issue was some grub errors, but I think that was just at first while the Ubuntu on the thumb drive got used to the idea of two hard disks that were not there on original install. I will post back if anything else goes wrong.

---

### Post by cjpbob on 2009-01-05
Yeah, I've noticed that it sometimes takes usb ubuntu a few boots to really get its footing, but after that it runs fairly smoothly. Congrats.

---

