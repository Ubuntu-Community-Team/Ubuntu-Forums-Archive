---
title: "dpkg error processing linux-server"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by Visko on 2008-09-21
Hey
I'm trying to get Ubuntu on my PC, but it always halts at the "install base components" part, somewhere around 84%.

In the other terminal (alt+f4) I see the following error message:

dpkg: error processing linux-server (--configure)
Errors were encountered:
linux-image_2.6.24-19-server
linux-ubuntu-modules-2.6.24-19-server
linux-image-server
linux-server

E: sub-process /usr/bin/dpkg return error code 1

I thought that my cd got corrupt during burning, so I burned the iso to another cd, and I still get the same error, at the same time.

What should I try?
My PC is an amd2600xp, with 2x750GB storage, and I'm trying the to install the latest server version. (ubuntu-8.04.1-server-i386.iso)

---

### Post by Pumalite on 2008-09-21
Error in post.

---

### Post by Visko on 2008-09-21
Should I enter this before I select "install base components" from the menu?

---

### Post by Pumalite on 2008-09-21
I misunderstood.
Burn a new CD. Do md5sum on iso, burn at 4x or less, check CD integrity before install. Do not use CD-RW. Clean the lens in your burner just in case. If you can; post:
sudo fdisk -lu

---

### Post by Visko on 2008-09-21
Will try in a moment, thank you.

---

### Post by Visko on 2008-09-21
Exact same error message, exact same time.
I have checked the md5 sum, and verified the contents of the cd, both correct.

---

### Post by Pumalite on 2008-09-21
What are your specs. Try to find out where the installation gets stuck.

---

### Post by Visko on 2008-09-21
It's an amd2600xp, on an asus P5VD2-VM/S motherboard, with 2 Western Digital hard drives.
The dvd-drive is a NEC 2650a, the VGA and LAN are integrated.

How should I start looking for the part where it fails?

---

### Post by Visko on 2008-09-22
Please help me :(

---

### Post by Visko on 2008-09-23
Bump

---

### Post by Pumalite on 2008-09-23
I supposed you are able to boot a Live CD.
Post:
sudo fdisk -lu

---

### Post by Visko on 2008-09-23
Right away:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00059242

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63       16064        8001   fd  Linux raid autodetect
/dev/sda2           16065  1465144064   732564000    5  Extended
/dev/sda5           16128    39086144    19535008+  fd  Linux raid autodetect
/dev/sda6        39086208    58621184     9767488+  fd  Linux raid autodetect
/dev/sda7        58621248    64484909     2931831   fd  Linux raid autodetect
/dev/sda8        64484973  1465144064   700329546   fd  Linux raid autodetect

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00062b0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63       16064        8001   fd  Linux raid autodetect
/dev/sdb2           16065  1465144064   732564000    5  Extended
/dev/sdb5           16128    39086144    19535008+  fd  Linux raid autodetect
/dev/sdb6        39086208    58621184     9767488+  fd  Linux raid autodetect
/dev/sdb7        58621248    64484909     2931831   fd  Linux raid autodetect
/dev/sdb8        64484973  1465144064   700329546   fd  Linux raid autodetect

Disk /dev/sdd: 1043 MB, 1043333120 bytes
255 heads, 63 sectors/track, 126 cylinders, total 2037760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06603c8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     2037759     1018848+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(125, 254, 63) logical=(126, 215, 25)

---

### Post by Visko on 2008-09-24
Bump :(

---

### Post by Visko on 2008-09-27
I have tried installing from an usb drive, as described in this page:
[https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller](https://help.ubuntu.com/community/UbuntuServerFlashDriveInstaller)

and it failed again at the linux-server image file.
It's definitely not a bad media.

---

### Post by lisati on 2008-09-27
> **Visko said:**
> It's an amd2600xp, on an asus P5VD2-VM/S motherboard, with 2 Western Digital hard drives.
The dvd-drive is a NEC 2650a, the VGA and LAN are integrated.

How should I start looking for the part where it fails?

What amount of RAM does it have?

---

### Post by Visko on 2008-09-27
It has a single stick of 1GB DDR ram. (Apacer)

---

### Post by Visko on 2008-09-28
YES!!!

I have tried installing without using raid, and it installed fine.
Now I just have to manually create the arrays somehow.

---

