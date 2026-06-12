---
title: "Ubuntu installation from Fedora: second drive issue"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by atoku on 2007-06-02
I bought a hard drive and installed on it Ubuntu. I had the previous same IDE drive in the system with Fedora Core 5 on it. The idea was to install Ubuntu, move data from previous IDE drive to the new one and then, use the old disk for different stuff. However, if I run from Ubuntu drive, it sees another IDE drive but claims it has a wrong partitions. If I start from Fedora Core, it also does not see partitions on Ubuntu drive.

Please, help!  I could not find any good info about it online!

---

### Post by confused57 on 2007-06-02
> **atoku said:**
> I bought a hard drive and installed on it Ubuntu. I had the previous same IDE drive in the system with Fedora Core 5 on it. The idea was to install Ubuntu, move data from previous IDE drive to the new one and then, use the old disk for different stuff. However, if I run from Ubuntu drive, it sees another IDE drive but claims it has a wrong partitions. If I start from Fedora Core, it also does not see partitions on Ubuntu drive.

Please, help!  I could not find any good info about it online!
Did you have the drive with Fedora connected when you installed Ubuntu on your new hard drive?  You might want to post both your Fedora and Ubuntu boot entries in your menu.lst, for Ubuntu:
```
gedit /boot/grub/menu.lst
```
and
```
gedit /boot/grub/device.map
```

then do the same, by posting your Fedora's boot configuration file.

Since you've been using Fedora, you probably already know how to access the file in Fedora(I don't know if it uses menu.lst or grub.conf).

You might also want to post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

---

### Post by atoku on 2007-06-02
The problem is "solved". I was able finally get the disk partitions when I reconnect drives to one bus and switch Ubuntu one to master mode and Fedora to slave mode.

I could not though make this with IDE1 and IDE2 2 master disks. I have no idea why. At least it works now!

Thanks for reply!

---

