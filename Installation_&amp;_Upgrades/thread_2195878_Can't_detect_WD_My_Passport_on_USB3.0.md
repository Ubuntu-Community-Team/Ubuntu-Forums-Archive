---
title: "Can't detect WD My Passport on USB3.0"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by barrymmm on 2013-12-26
I'm having the [same problem]("http://ubuntuforums.org/showthread.php?t=2193494"). I've got a WD My Passport 1GB external hard drive and I can't seem to detect it on my USB 3.0 port. It works fine on my USB 2.0 ports.
I've got a Lenovo Y500 with Ubuntu Linux 3.11.0-14-generic
 Here's what I got for those commands:
lsusb
```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bda:58dd Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

sudo fdisk -lu 

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    31277231    15638615+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006c8df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux

sudo fdisk -lu
[sudo] password for barry: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 16.0 GB, 16013942784 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31277232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1    31277231    15638615+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006c8df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953523711   976760832   83  Linux
```

ls -l /media
```
total 100
drwxr-x---+ 2 root root 4096 Dec 26 18:18 laptop
drwxr-x---+ 2 root root 4096 Oct 31 16:04 guest-0a4Jnf
drwxr-x---+ 2 root root 4096 Nov  7 20:47 guest-5SZjvT
drwxr-x---+ 2 root root 4096 Nov  5 22:32 guest-ACMw9w
drwxr-x---+ 2 root root 4096 Nov  7 20:02 guest-c3oVeL
drwxr-x---+ 2 root root 4096 Nov  2 09:47 guest-DZC8bC
drwxr-x---+ 2 root root 4096 Nov  7 16:03 guest-E3jF3x
drwxr-x---+ 2 root root 4096 Nov  6 16:10 guest-FPpjZ2
drwxr-x---+ 2 root root 4096 Nov  7 19:17 guest-hwtJnn
drwxr-x---+ 2 root root 4096 Nov  8 12:45 guest-knUVw8
drwxr-x---+ 2 root root 4096 Nov  9 16:01 guest-LCtcT9
drwxr-x---+ 2 root root 4096 Nov  8 20:39 guest-mFBDGV
drwxr-x---+ 2 root root 4096 Nov  2 14:49 guest-mkiTlL
drwxr-x---+ 2 root root 4096 Nov  9 17:53 guest-oQ4Ou2
drwxr-x---+ 2 root root 4096 Nov  9 09:21 guest-qCZ0JO
drwxr-x---+ 2 root root 4096 Oct 29 15:49 guest-tpY2sN
drwxr-x---+ 2 root root 4096 Oct 30 16:21 guest-tRJCde
drwxr-x---+ 2 root root 4096 Nov  7 20:08 guest-vqcdKx
drwxr-x---+ 2 root root 4096 Nov  4 15:35 guest-vqwO3s
drwxr-x---+ 2 root root 4096 Nov  3 23:24 guest-W29dH6
drwxr-x---+ 2 root root 4096 Nov  9 18:09 guest-wkas25
drwxr-x---+ 2 root root 4096 Oct 29 15:51 guest-wuVf6D
drwxr-x---+ 2 root root 4096 Oct 28 21:33 guest-WZSfQT
drwxr-x---+ 2 root root 4096 Nov  7 16:01 guest-yXiYAR
drwxr-xr-x  2 root root 4096 Apr  1  2013 home
```

I've tried just plugging it into the USB 3.0 port and the light on the device comes on but that's about it. I've tried booting with it plugged in and it's the same. Looks like the hardware is ok but Ubuntu can's see it. Any suggestions.
p.s. The laptop has a hybrid drive 16GB SSD (sda) for the OS and the 1TB HDD (sdb) for data
When I plug it into a USB 2.0 port it is detected immediately as sdc

---

### Post by barrymmm on 2014-01-06
bump

---

