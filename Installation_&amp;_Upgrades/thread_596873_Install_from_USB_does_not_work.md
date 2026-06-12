---
title: "Install from USB does not work"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by hoborocket on 2007-10-30
I followed the instructions listed here exactly: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

It just gives me "operating system not found" when I try to boot from the USB drive.

This is extremely frustrating, as I have no other way to install.

I am using a Fujitsu ST4110 tablet PC with no optical drives.

---

### Post by hoborocket on 2007-10-30
Nobody has any idea? Is this that difficult a question?

---

### Post by hoborocket on 2007-10-31
I am following the directions here:

[https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html)

I format my USB drive as a single FAT16 partition. I do  zcat boot.img.gz > /dev/sdb1 s directed, and it turns the drive into this:

[http://img228.imageshack.us/img228/2481/whatthechristyh1.png](http://img228.imageshack.us/img228/2481/whatthechristyh1.png)

What do I do?

---

### Post by kbyrd on 2007-11-09
I did this:
- got a usb drive, /dev/sdc
- partioned it with a single bootable partition.
- unzipped the boot.img.gz <---- This might be the diff
- dd if=/tmp/boot.img of=/dev/sdc1
- install-mbr /dev/sdc

Rebooted and it worked!

---

