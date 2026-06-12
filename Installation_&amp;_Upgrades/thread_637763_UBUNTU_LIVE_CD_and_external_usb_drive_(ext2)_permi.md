---
title: "UBUNTU LIVE CD and external usb drive (ext2) permission problem"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by 10000V on 2007-12-11
I use Ubuntu Live CD 6.10 on an laptop.

I would like to access to an fresh new created ext2 partition (with full read write) access on my external USB2 hard drive.
By default, after booting over the Ubuntu Live CD, this isn't possible!
I have only read access to the external USB drive?

I have tried to configure the USB drive by clicking (right-click) on the USB desktop Icon and then selecting "Properties" and then the"Volume Tab". Here, the user, has the possibility to change the USB drive mounting parameters.

The default Ubuntu parameters which gives only read access are

Mounting point :    /media/EXT2XX
Filesystem : ext2
Mount options :    rw nosuid nodev


I tried to mount the usb with following parameters:

Mounting point :    /media/EXT2XX
Filesystem : ext2
Mount options :    rw,noauto,user,exec 0 0

When trying to mount my drive with this parameters I get the following error message:
```

Impossible to mount the volume <<EXT2XX>>
Details
mount_point cannot contain the following
characters:newline, G_DIR_SEPARATOR (usaly /)
```

With which options should my external USB drive be setup in order to get full read/write access to it?

Thanks for helping.

---

### Post by logos34 on 2007-12-11
post the output of 

**sudo fdisk -l** (i.e. lowercase L)

Try mounting it as root from the terminal.  For example, if the usb drive shows up as '/dev/sdb', then

sudo mkdir /media/ext2xx

sudo mount -t ext2 /dev/sdb /media/ext2xx

try to save something to it.

---

### Post by 10000V on 2007-12-11
Thanks for helping ...:)
Here's the output of << sudo fdisk -l >>
> ubuntu@ubuntu:~$ sudo fdisk -l

Disque /dev/sda: 120.0 Go, 120034123776 octets
255 heads, 63 sectors/track, 14593 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdea9dea9

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1         510     4096543+  1b  Hidden W95 FAT32
/dev/sda2   *         511        7806    58605120    7  HPFS/NTFS
/dev/sda3            7807       14593    54516577+   f  W95 Etendu (LBA)
/dev/sda5            7807       14593    54516546    b  W95 FAT32

Disque /dev/sdc: 250.0 Go, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sdc1   *           1       26356   211704538+   c  W95 FAT32 (LBA)
/dev/sdc2           26357       30401    32491462+  83  Linux
ubuntu@ubuntu:~$

I have mounted the USB device manually with the command you had suggested:
> sudo mount -t ext2 /dev/sdc2 /media1/ext2XX

At this stage I have still only read access?

I have also tried following command without getting write access to the usb ext2 drive partition:
> sudo mount -t auto -o exec,suid /dev/sdc2 /media1/EXT2XX

---

### Post by logos34 on 2007-12-11
ok, so you're using '/media[COLOR="Red"]1[/COLOR]..

umm...try changing ownership and/or permissions

**ls -l /media1/EXT2XX** or whatever it is

sudo chmod -r 777 /media1/EXT2XX
sudo chown -r <username>:<username> /media1/EXT2XX  (where 'username'=yours)

---

### Post by aonegodman on 2007-12-11
Very interesting. May I interject a question here for this newby. Would you please explain the terminology "sudo" and how and where it is used? I take it that it is some type of system comand that would be run similarly in Windows under the Command Prompt. Being new to linux I need some help here. Is this function entered in a terminal program? For example the following comment from above states:

"post the output of

sudo fdisk -l (i.e. lowercase L)"

I find this and similar comments throughout forum responses and have yet to find how to use them. Any help or guidance is appreciated. Thank you.

---

### Post by logos34 on 2007-12-11
> **aonegodman said:**
> Very interesting. May I interject a question here for this newby. Would you please explain the terminology "sudo"....

here's a pretty full explanation:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aonegodman on 2007-12-11
Thanks for pointing the way logos34. That's what I needed. :)

---

### Post by 10000V on 2007-12-11
I finally got the writing access by using the command:

> sudo chmod 777 /media1/ext2XX

LOGOS34 thanks for your help. :guitar:

---

