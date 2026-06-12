---
title: "problem mounting 2nd hard disk"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by rbms on 2006-09-29
I installed Ubuntu a week ago.
When I try to mount my second hard drive "sudo mount -t ext3 /dev/hdb1 /mnt/secondHDD/", I get following error 
"mount: /dev/hdb1 already mounted or /mnt/secondHDD/ busy"
I am sure I did not mount my second hard drive. 

The "Disk Manager " says that the disk is Inaccessible, with unknown file system (I booted my system using ubuntu CD and mkfs -t ext3 /dev/hdb1). I cannot enable it or format it from Disk Manager.

In the Device Manager, following are details for my second hard drive.
    IDE device (slave)
     |--WDC WD800BB-00CAA1
       |--Volume (ext3)
       |--volume (ext3)
The Device Manager says that volume is not mounted.

After I installed ubuntu I compiled my kernel to "2.6.17.13".

Following is what is present in my mtab and fstab. 

$ cat /etc/mtab
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Any help is appreciated.

---

### Post by rbms on 2006-09-29
I fixed the isssue. Had to uninstall evms package. Don't know why

[http://www.debianhelp.org/node/1296](http://www.debianhelp.org/node/1296)

---

