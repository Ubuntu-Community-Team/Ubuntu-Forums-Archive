---
title: "USB with Loopback"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by wanfahmi on 2008-02-12
I'm using a 4GIG USB Flash drive. I'm doing this so that I can use the free space to store other files and make accessible in Windows. 
I'm trying to make this setup:
Partition 1: /dev/sdb1 FAT32. with 512MB casper-rw [loopback]("https://help.ubuntu.com/community/LiveCDPersistence") file
Partition 2: /dev/sdb2 FAT16 with Ubuntu (Installed as per [this guide]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")

This is my syslinux.cfg
```

DEFAULT vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in USB persistent mode (saves changes) 
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz quiet splash --
LABEL live
  menu label ^Start Ubuntu in Live mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

I've done the normal USB persistence installation with success. 
I'm unable to get Ubuntu to boot from the second partition. I'm able to get ASH. I'm guessing I need to fix syslinux.cfg. Can somebody point out a way to do this?

I think I need to make this section point to the second partition but I don't know how.
```

LABEL persistent
  menu label ^Start Ubuntu in USB persistent mode (saves changes) 
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz quiet splash --
```

**_What I've tried_**
Changing to **file=/dev/sdb2/preseed/ubuntu** doesn't seem to work.

---

### Post by wanfahmi on 2008-02-13
Bump

---

