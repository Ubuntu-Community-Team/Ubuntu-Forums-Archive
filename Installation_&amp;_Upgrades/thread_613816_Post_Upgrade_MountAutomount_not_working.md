---
title: "Post Upgrade Mount/Automount not working"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by theonlyalterego on 2007-11-15
My Problem: IDE (2 drives) and SATA (1 drive) drives will not mount, umount, auto-mount or pmount post upgrade
What changed: I used the standard ubuntu 'upgrade' to move to the newest kernel 

I believe what's going on is the new kernal is locking the drives up.
Here: [http://tinyurl.com/28j63j](http://tinyurl.com/28j63j)
and here: [http://tinyurl.com/2lrsay](http://tinyurl.com/2lrsay)

both make me think that these packages may be included with the new upgrade, and are somehow screwing things up for me. Here's part of my kern.log:
```

Nov 15 10:33:24 localhost kernel: [   58.526528] device-mapper: table: 254:3: linear: dm-linear: Device lookup failed
Nov 15 10:33:24 localhost kernel: [   58.526536] device-mapper: ioctl: error adding target to table

```
there are a ton of lines like this immediately after it mounts the main drive. Here's my mount umount pmount results:
```

me@ub-desktop:/$ sudo mount -t ntfs /dev/sda1 /media/sata1
[sudo] password for me:
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 (Local disk)

me@ub-desktop:/$ sudo pmount /dev/sda1
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda1 (Local disk)

me@ub-desktop:/$ sudo umount /dev/sda1
umount: /dev/sda1: not mounted

me@ub-desktop:/$ umount /dev/sda1
umount: /dev/sda1 is not mounted (according to mtab)

```

I get the same errors for my other 2 IDE drives:
```

me@ub-desktop:/$ sudo mount -t ext3 /dev/hdc1 /media/disk3
mount: /dev/hdc1 already mounted or /media/disk3 busy

```

here's my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=5efe5a0f-bfef-4488-868d-b8f173f823bd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=8cdc5609-59ea-41e1-a164-107819a2dc7f none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hdb1 -- converted during upgrade to edgy
UUID=f72bb4d2-77c2-4588-9183-19698e794bf3 /media/disk2 reiserfs defaults 0 0
# automount SATA drive
/dev/sda1 /media/sata1 ntfs-3g defaults,locale=en_US.utf8 0 0
# automount disk3 - storage
/dev/hdc1 /media/disk3 ext3 defaults 0 0
# automount ipod
/dev/sdb2 /media/ipod vfat user,noauto,umask=000 0 0

```

here's an ls of my /media dir:
```

me@ub-desktop:/$ ls -al /media
total 36
drwxr-xr-x  9 root root 4096 2007-11-15 10:33 .
drwxr-xr-x 21 root root 4096 2007-11-10 01:41 ..
lrwxrwxrwx  1 root root    6 2006-09-27 15:23 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2006-09-27 15:23 cdrom0
drwxr-xr-x  2 root root 4096 2007-06-18 17:35 disk2
drwxrwxrwx  2 root root 4096 2007-07-12 11:07 disk3
drwxr-xr-x  2 root root 4096 2007-11-12 02:51 disk3_1
-rw-r--r--  1 root root    0 2007-11-15 10:33 .hal-mtab
drwxr-xr-x  2 root root 4096 2007-08-09 22:11 ipod
drwxrwxrwx  2 root root 4096 2007-07-19 23:40 sata1
drwxr-xr-x  2 root root 4096 2007-07-12 11:07 windisk2

```

Ubuntu was nicely auto-mounting these drives before I upgraded, and (I believe) it was using the entries in my fstab to do this.

[edit2] here's my fdisk results btw if that helps
```

me@ub-desktop:~$ sudo fdisk -l
[sudo] password for me:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02f31306

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hda: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e910e91

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1190     9558643+  83  Linux
/dev/hda2            1191        1244      433755    5  Extended
/dev/hda5            1191        1244      433723+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ee1160c

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161   42  SFS

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04b57ae7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4864    39070048+  83  Linux

```
[/edit2]

So I have two questions:
1) has anyone else seen this problem, and is there a solution?
2) how do i remove "md-mapper, md-mod and dm" modules from my kernal? I've been using linux for a while, but never recompiled my own kernel... any help would be appreciated if that [edit1. finishing sentance =P] is the recommended solution.[/edit1]

---

### Post by milwell on 2007-11-20
I'm also having same problems with 7.10, 
I had a clean install, after that I setup LDAP client authentication
I didn't notice the cdrom is not automounting prior to LDAP, but i think it automounted because when I installed LDAP,...etc using synaptic, it asked for the Gutsy Gibbon CD, and I loaded it and it went fine.

Are you using LDAP authentication?
Is this an LDAP authentication issue?

---

