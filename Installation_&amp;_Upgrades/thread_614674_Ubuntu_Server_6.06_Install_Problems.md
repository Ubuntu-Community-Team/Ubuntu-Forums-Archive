---
title: "Ubuntu Server 6.06 Install Problems"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by johnc2k on 2007-11-16
:confused:

Ive just tried installing Ubuntu Server 6.06 on my PC but I get the following problem:

Ive ran the installer, and installed it to a single 250GB SATA Drive, (I also have 2x80GB Drives which I want to use as Raid 0 but I have not configured them yet.)
The install appeared to complete fine, I remove the CD as instructed, the PC reboots, and now on startup I get the following error:
```


Booting 'Ubuntu, kernel 2.6.15-26-server'

root   (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /boot/vmlinuz-2.6.15-26-server root=/dev/sda1 ro quiet splash
   [Linux-bzImage, setup=0x1x00, size=0x16c98f]
initrd   /boot/initrd.img-2.6.15-26-server
   [Linux-initrd @ 0x1f94e000, 0x6a14c5 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
[42949380.590000] ata3: disabling port
ALERT! /dev/sda1 does not exist. Dropping to a shell!


BusyBox v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#


```

Ive tried typing FDisk, but it just says 'fdisk: not found'.

Any help would be great!

Thanks

John

---

### Post by Sef on 2007-11-16
Here's how one op [solved]("http://www.linuxquestions.org/questions/ubuntu-63/binsh-cant-access-tty-job-control-turned-off-474493/page2.html") their problems with busybox (post #16.)

If that don't help, then use this in ask or google:  > /bin/sh: can't access tty; job control turned off.

---

