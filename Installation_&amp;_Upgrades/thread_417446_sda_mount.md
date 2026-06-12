---
title: "sda mount"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by bearcat on 2007-04-21
For the most part my Feisty install went fine once I was able to find a decent mirror to download from. I have come across one quirk that I don't know how to correct, though: I now have *two* icons on my desktop for my Windoze partition. 

The first one is labelled sda1, and if I try to unmount it I get the error message that I can't because it wasn't mounted by me. The second one is labelled sda1(2), and if I try to unmount that one the error message I get is > [mntent]: warning: no final newline at the end of /etc/fstab
umount: /media/sda1 mount disagrees with the fstab 

If I go into the mount directory, meanwhile, *only* the mount labelled as sda1(2) actually shows up in there. But from the desktop, I can get into the Windows partition just the same from either icon.

Can anybody tell me how to get the duplicate icon off my desktop?

---

### Post by bwhite82 on 2007-04-21
Hi, do this:

> sudo gedit /etc/fstab

Copy the contents, and paste in a reply here.

---

### Post by bearcat on 2007-04-21
Here goes...

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=d972cfe3-29e8-403f-b793-c55cfb323129 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=549470FD9470E2C2 /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=bfaaa969-7672-480d-8bd6-2c7f5c00aed8 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by bwhite82 on 2007-04-21
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda2 -- converted during upgrade to edgy
UUID=d972cfe3-29e8-403f-b793-c55cfb323129 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
/media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=bfaaa969-7672-480d-8bd6-2c7f5c00aed8 none swap sw 0 0
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

First make a backup of this file:

> sudo cp /etc/fstab /home/YOURUSERNAME

Then try removing that "UUID" entry like the above example, I do not have this in my fstab, for reference, here is mine:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/sda2       /media/windows  ntfs    rw,users,umask=022  0      0
/dev/sda1       /media/sda1     vfat    defaults        0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/thumb    auto        rw,user
0       0

---

### Post by bearcat on 2007-04-21
Great, that did it. Thanks!

---

