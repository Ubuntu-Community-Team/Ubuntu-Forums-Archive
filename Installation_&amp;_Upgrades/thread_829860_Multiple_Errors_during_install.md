---
title: "Multiple Errors during install"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by connord94 on 2008-06-15
OK, I'm trying to install Ubuntu to my 80gb external (USB) hard drive.

The first problem I got was when the actual *installation* started, I got something like:

Blah Blah Blah Failed because Could not be unmounted:

/media/LaCie\ DriveDrive

Then when I cancel and try to install again, when the partition manager begins to start I get:

PartMan failed with exit code 10


I have had similar problems ejecting the drive in XP, and The ubuntu live CD, but not vista, where it says I cannot eject/unmount the drive because it is in use, then the second time I try to eject it it does so perfectly.

The drive is formatted in NTFS - but the Ubuntu installer formats it to Ext3 anyway so ..?


Help installing it will be greatly appreciated


Connor

---

### Post by connord94 on 2008-06-15
Sorry for the double post, but the above problems have been solved after a simple restart, but the initial installation problem came back after a re-attempt. I get the OS selection menu, when I click Ubuntu I get:

```
Error 22:No Such Partition
```


Any help?


Connor

<<EDIT>>

OK, so, I know how to solve it, but need help with the numbers.

I know I need to change the something in grub, but I don't know what to change it to.

The default is (hd1,4)

Yet I'm using an external drive,
In the live CD fdisk gives me :
(for the drive linux is installed on)

sdb1 * <all of the block crap> HPFS/NTFS
sdb2   <"  "  "  "  "  "  "  > Extended
sdb5   <"  "  "  "  "  "  "  > Linux
sdb6   <"  "  "  "  "  "  "  > Linux Swap/Solaris

What do I need to change the (hd1,4) to ?


Cheers,
Connor

---

