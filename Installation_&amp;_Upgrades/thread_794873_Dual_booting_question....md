---
title: "Dual booting question..."
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by kupo365 on 2008-05-15
Primary 0 Ubuntustudio
Primary 1 NTFS (music, pics, vids)
Secondary 0 CDROM
Secondary 1 Windows Xp

What do I enter in the menu.lst for the Grub to dual boot Ubuntu and Windows?

title Microsoft Windows XP
root (hd*,*)
savedefault
makeactive
map (hd*) (hd*)
map (hd*) (hd*)
chainloader +1

Thanks

---

### Post by iaculallad on 2008-05-15
Could you post whatever comes when you execute this for additional details:

sudo fdisk -l

---

### Post by kupo365 on 2008-05-15
> **iaculallad said:**
> Could you post whatever comes when you execute this for additional details:

sudo fdisk -l

Right Herrre

> Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb64db64d

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4660    37431418+  83  Linux
/dev/hda2            4661        4865     1646662+   5  Extended
/dev/hda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb64db64d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/hdd: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x264e264d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2490    20000893+   7  HPFS/NTFS


---

### Post by iaculallad on 2008-05-15
To re-create your GRUB:

mount /dev/hdb1 /mnt grub-install --root-directory=/mnt '(hd0)'

---

### Post by confused57 on 2008-05-15
You might also want to post the output of:
```
gedit /boot/grub/device.map
```

---

### Post by kupo365 on 2008-05-15
> **confused57 said:**
> You might also want to post the output of:
```
gedit /boot/grub/device.map
```

I get this
> 
(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hdd

---

### Post by iaculallad on 2008-05-15
mount /dev/hda1 /mnt grub-install --root-directory=/mnt '(hd0)'

to recreate your GRUB Menu list. This will load Ubuntu's menu enabling you to select loading either Ubuntu or windows.

if it fails: try sudo update-grub

---

### Post by kupo365 on 2008-05-15
> **iaculallad said:**
> mount /dev/hda1 /mnt grub-install --root-directory=/mnt '(hd0)'

to recreate your GRUB Menu list. This will load Ubuntu's menu enabling you to select loading either Ubuntu or windows.

if it fails: try sudo update-grub

Ok, I did that and got 
> 
bren@studio:~$ sudo mount /dev/hda1 /mnt grub-install --root-directory=/mnt '(hd0)'
mount: unrecognized option `--root-directory=/mnt'
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


So I put only 1 - before root-directory and got

> bren@studio:~$ sudo mount /dev/hda1 /mnt grub-install -root-directory=/mnt '(hd0)'
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


I think it's missing something

---

### Post by confused57 on 2008-05-16
It appears grub recognizes your Windows drive as (hd2)
> (hd0) /dev/hda
(hd1) /dev/hdb
(hd2) /dev/hdd

This might work for booting Windows:
```
title  Windows XP
root  (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

---

