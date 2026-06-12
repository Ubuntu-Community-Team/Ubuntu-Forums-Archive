---
title: "No boot option"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by changes on 2008-01-09
Hi all.

I have installed Ubuntu 7.10 on mye laptop HpCompac NC8000 on my second partition (WinXP on first (C:))
But after installation of Ubuntu I got no choice of Booting to Ubuntu when I reboot my machine.
It boots straight in to WinXP.
I have reinstalled trying to solve the problem, but that didn't help.

So I'm up to some good answers here :D

---

### Post by Pumalite on 2008-01-09
Can you boot a Live CD? If you do, post:

sudo fdisk -lu (from the Terminal)

You can also try reinstalling Grub.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by changes on 2008-01-09
That's what I call a fast answer, thx
Can Boot the Live Cd yes, so I wil try your sugestion

---

### Post by changes on 2008-01-09
Nope, did not work :(

---

### Post by bigmakms on 2008-01-09
Hey i have the ordered cd but when i reboot my computer it doesnt even like show that the cd is in there it doesnt boot ubuntu and i have windows 200 xp what should i do?

---

### Post by Pumalite on 2008-01-09
> **changes said:**
> Nope, did not work :(

Post your:

sudo fdisk -lu

---

### Post by changes on 2008-01-09
> **Pumalite said:**
> Post your:

sudo fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b9b4b9a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   113111007    56555472+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       113113665   117210239     2048287+   5  Extended
/dev/sda5       113113728   117210239     2048256   83  Linux

Disk /dev/sdb: 4110 MB, 4110228480 bytes
16 heads, 63 sectors/track, 7964 cylinders, total 8027790 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     8027789     4013863+   b  W95 FAT32

Disk /dev/sdc: 60.0 GB, 60011642368 bytes
255 heads, 63 sectors/track, 7295 cylinders, total 117210239 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   117194174    58597056    7  HPFS/NTFS

Disk /dev/sdd: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5d19c257

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1           16065    78124094    39054015    f  W95 Ext'd (LBA)
/dev/sdd5           16128    78124094    39053983+   7  HPFS/NTFS

---

### Post by Pumalite on 2008-01-09
We'll assume your Ubuntu is in sda5

Booting the Live CD, at the Terminal:

sudo mkdir /media/sda5

sudo mount -t ext3 dev/sda5 /media/sda5

From that partition, post:

cat /boot/grub/menu.lst

(is it's somewhere else, change accordingly)

---

### Post by changes on 2008-01-09
> **Pumalite said:**
> We'll assume your Ubuntu is in sda5

sudo mount -t ext3 dev/sda5 /media/sda5



(is it's somewhere else, change accordingly)

That command shows me
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/sda5/media/sda5
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by Pumalite on 2008-01-09
Sorry, my mistake.

sudo mount -t ext3 /dev/sda5 /media/sda5

(copy and paste)

---

### Post by changes on 2008-01-10
Problem solved:

Looks like the 2GB partition was to small, tough  it is the requirements for installing I think.
Anyway, I reduced my WinXP partition with 2GB, so Ubuntu now have 4 GB.
Installation went smooth and bootloader works as it should.
Thanks for your help anyway.

Changes

---

