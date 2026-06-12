---
title: "Upgrade from 12.04 to 12.10 server, Grub broken"
date: 2012-12-18
forum: Installation &amp; Upgrades
---

### Post by Phil35 on 2012-12-18
Hi,
I upgrade two PC at home without any problem, however I got problems with the third.

[http://paste.ubuntu.com/1448018/](http://paste.ubuntu.com/1448018/)

As you can see, I used ubuntu-secured-remix to try to correct the problem ... with no success with the use of boot-repair

sdba : disk with ubuntu install and this is where is the problem
sdbb : disk with data / backup of my camera
sdbc : usb key.

How is it posssible to reinstall grub on this  PC ? 

Any help will be greatly appreciated !
Kind regards
Phil

---

### Post by YannBuntu on 2012-12-18
Hi Phil
try Boot-Repair --> Advanced options --> GRUB location tab --> tick "Separate /boot: sda1" --> Apply

---

### Post by Phil35 on 2012-12-19
Hi,
the option doesn't work ...
So I spent time on this problem, as I don't want to reinstall :-)
I found and correct.

The boot-repair didn't work as expected

I usedurl=http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/]restoring-grub-for-an-encrypted-lvm[/url]
I don't know what is the root cause of the fatal error during upgrade from 12.04 to 12.10, however I suspect the upgrade program got the same kind of problem as boot-repair.

sda1 : /boot     but it is an old one .. from Fedora 7.  The PC ran several years with fc7, before I install Ubuntu 12.04
sda2 : / LVM    there is a /boot included inside 

I think the problem came from the two /boot. One visible easily and the other in the LVM. Programs got confused

Here under is the correction if it can help others : 

On another pc, create of a usk bootable key using the program  "disk creator"  (and ubuntu secured remix 12.10 32-bit)
Program used  : plpbm (boot manager) [plp bm](http://download.plop.at/files/bootmngr/plpbt-5.0.14.zip)
It is possible then to boot on this usb key. 
The  pc (Intel Pentium 4 , 2.0Ghz) doesn't allow to boot on a usb key.
PLPBM : very efficiency program !

Then, after boot ALT CTRL F1  ...  and go to console mode  :-)
```
# fdisk -l /dev/sda

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78156288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x94c394c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *      208845    78156224    38973690   8e  Linux LVM

``` 
I deleted sda1 with cfdisk program (don't forget to write before existing)
then:
```

# pvscan
  PV /dev/sda2   VG VolGroup00   lvm2 [37.16 GiB / 64.00 MiB free]
  Total: 1 [37.16 GiB] / in use: 1 [37.16 GiB] / in no VG: 0 [0   ]

# lvscan
  ACTIVE            '/dev/VolGroup00/LogVol00' [24.41 GiB] inherit
  ACTIVE            '/dev/VolGroup00/LVvar' [4.88 GiB] inherit
  ACTIVE            '/dev/VolGroup00/LVhome' [6.81 GiB] inherit
  ACTIVE            '/dev/VolGroup00/LogVol01' [1.00 GiB] inherit

```
The /boot is in the LV  VolGroup00/LogVol00
```
 
# mkdir /media/linux
# mount /dev/VolGroup00/LogVol00 /media/linux
# mount /dev/VolGroup00/LVvar /media/linux/var
# mount /dev/VolGroup00/LVhome /media/linux/home
# mount -o bind /proc /media/linux/proc
# mount -o bind /dev /media/linux/dev
# mount -o bind /sys /media/linux/sys

```
then
```

chroot /media/linux /bin/bash

```
and  
```

grub-mkconfig -o /boot/grub/grub.cfg
grub-install --grub-setup=/bin/true /dev/sda

```

reboot and Ok
Yes !

After usual update and upgrade, under 12.10, program hostapd was updated to version 1, which is code for my access point !
```

# hostapd -v
hostapd v1.0
User space daemon for IEEE 802.11 AP management,
IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator
Copyright (c) 2002-2012, Jouni Malinen <j@w1.fi> and contributors

```

Kind regards
Phil

---

