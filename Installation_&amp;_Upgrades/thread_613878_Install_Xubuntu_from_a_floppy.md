---
title: "Install Xubuntu from a floppy"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by mrmonday on 2007-11-15
My friend has an old laptop, and I have been assigned the task of installing Xubuntu on it for them. The problem is that the laptop only has a built in floppy drive. I have an external USB CD-ROM drive, but the bios can't boot from it. I have tried using the smart boot manager, but it doesn't recognise the external drive. I have downloaded tomsrtbt linux, and put it on a floppy which the BIOS will boot. Is it possible to use tomsrtbt to mount the external CD drive and boot from it? If not is there any other way of getting Xubuntu on it? I would rather not use wubi, as they would like to remove windows.

---

### Post by maybeway36 on 2007-11-15
I think Debian has netinst floppy images:
[http://www.us.debian.org/distrib/netinst#verysmall]("http://www.us.debian.org/distrib/netinst#verysmall")

---

### Post by mrmonday on 2007-11-15
Will this work with Xubuntu? Does it support USB CD-ROM drives?

---

### Post by logos34 on 2007-11-15
Unfortunately SBM doesn't support USB boot. (you'd think they would have added that capability by now--how hard can it be?).  Never tried tomsrtbt.  Trying to figure out a way to install from a usb cd drive with a non-usb boot Bios is a real bummer.

You know, you can go the Wubi route and convert it using LVPM to a permanent install on a dedicated partition, then delete windows:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

It might be easier though to start up a network install from windows using this method:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)

(there's even a section 'CD approach' in the latter that boots from the hard disk first and follows through on cd--might work with your usb-cdrom.)

---

