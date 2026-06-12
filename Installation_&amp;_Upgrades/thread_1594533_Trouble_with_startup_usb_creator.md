---
title: "Trouble with startup usb creator"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dustyg54 on 2010-10-12
I am trying to use the usb startup creator to make a xubuntu 10.10 ( with downloaded .iso) startup disk to a 2gb flash drive.  I formatted the drive to ext4, and when I start the usb creator I get this error: "Failed to install the bootloader."  

1. Should I have formatted the drive to ext4? In the usb creator instructions the author used ext3 as an example.
2. I am using the 64bit .iso file. I am trying to make the drive from a 64bit pc running ubuntu 10.04 (64bit).
3. If I can get this to work, will the 64bit flash drive then boot using a 32bit pc?  (I wouldn't want to install it, but rather boot to use as a portable OS.) 

Thanks,
Dusty

---

### Post by C.S.Cameron on 2010-10-12
Startup Disk Creator requires a flash drive formatted in FAT, FAT32 seems to work best for me.
32 bit is probably best for booting multiple computers.

---

### Post by dustyg54 on 2010-10-13
That worked!  Posting from the flash drive now.  Thanks!

---

### Post by Gilthans on 2011-08-21
This solved for me as well. Seems prudent to either:
a) format the disk, since all data is lost anyway;
b) show an error message informing that the disk should be FAT32...

---

### Post by maniandram on 2012-07-22
It need FAT because the isolinux needs it i think.:P too bad it doesnt support ext4 :(

---

