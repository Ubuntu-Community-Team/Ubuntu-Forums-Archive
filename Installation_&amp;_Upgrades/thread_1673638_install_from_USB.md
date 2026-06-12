---
title: "install from USB"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2011-01-22
Hi there.
I'm trying to install Ubuntu Server 10.10 from USB to a computer without CDROM. The installation fails trying to detect the CDROM.
Do I need a CDROM for installing U.Server from USB?
Thanks a lot!

---

### Post by dabl on 2011-01-22
Is that a Sandisk USB stick, with the U3 "CD ROM" hidden partition?  Those can be difficult.  If that is what it is, I would advise use dd on it:

```
sudo dd if=/dev/zero of=/dev/sd*x* bs=1 count=512
```

and make sure *x* is the actual partition ID of the USB stick and _not_ a hard drive partition!

This will destroy all data and the partition table.  Use GParted to make a new MS-DOS partition table, and then make a FAT32 partition on it, and then you will need to set it up with the Ubuntu installer again.

---

### Post by hirohitosan on 2011-01-22
thanks dabl. Its a U3 USB pendrive.
I did all you sugested but after rebooting the installation failed again searching for CD. I'll try with another pendrive

---

### Post by dabl on 2011-01-23
I have 5 Sandisk USB sticks.  4 of them work right after I dd'd them, but one has the U3 partition that I cannot get rid of.  They are tricky.

---

