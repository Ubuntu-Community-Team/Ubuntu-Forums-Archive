---
title: "Windows 7 and GRUB2?"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by SilverSnakeEyes on 2010-07-17
After installing ubuntu 10.4 netbook remix edition to my laptop, I then found that GRUB hadn't installed at all, and it went straight to windows 7 each time. So I rebooted from my live-usb and got into the terminal, and typed 
```

sudo grub-install /dev/sda5

```
which then gives me
```
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

```

Can anyone help me out?

---

### Post by SilverSnakeEyes on 2010-07-17
Using fdisk and GParted, I come to find out that the NTFS partition for windows 7 is screwed up now :(

```
GParted 0.5.1
 Libparted 2.2
    Check and repair file system (ntfs) on /dev/sda2  00:00:05    (  ERROR )             calibrate /dev/sda2  00:00:00    ( SUCCESS )             path: /dev/sda2
start: 206848
end: 215059619
size: 214852772  (102.45 GiB)          check file system on /dev/sda2 for errors and (if possible) fix  them  00:00:05    ( ERROR )             ntfsresize -P -i -f -v /dev/sda2             ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda2
NTFS  volume version: 3.1
Cluster size       : 4096 bytes
Current  volume size: 110004613632 bytes (110005 MB)
Current device size:  110004619264 bytes (110005 MB)
Checking for bad sectors ...
Checking  filesystem consistency ...
Accounting clusters ...
***(I cut all the cluster parts out, its a really long list.)***
Filesystem  check failed! Totally 899 cluster accounting mismatches.
ERROR: NTFS  is inconsistent. Run chkdsk /f on Windows then reboot it TWICE!
The  usage of the /f parameter is very IMPORTANT! No modification was
and  will be made to NTFS by this software until it gets repaired.
            ========================================

```

---

### Post by whit on 2010-07-18
> **SilverSnakeEyes said:**
> After installing ubuntu 10.4 netbook remix edition to my laptop, I then found that GRUB hadn't installed at all, and it went straight to windows 7 each time. So I rebooted from my live-usb and got into the terminal, and typed 
```

sudo grub-install /dev/sda5

```

Wouldn't that be installing grub onto /dev/sda5 rather than the master boot record?

---

