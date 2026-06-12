---
title: "How to copy file from thumb driver from console"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by richardmems on 2008-11-17
Hello

How can i access to the CD-ROM and thumb drives from Linux terminal or Console without using GUI file browser?

Thanks

---

### Post by Partyboi2 on 2008-11-17
Use 
```
cd /media/cdrom
``` to move into the cdrom directory and use
```
ls
``` to view contents
If it is not mounted you can  mount it (should be though) by
```
sudo mount /media/cdrom
``` For you thumb drive check
```
sudo fdisk -l
``` to find the device, it probably be something like /dev/sdb? Once you know what one it is make a mount point
```
 sudo mkdir /media/thumb
```then mount it
```
sudo mount /dev/sdc? /media/thumb
``` Replace /dev/sdc? with the correct one from the fdisk -l output, then 
```
cd /media/thumb
```You can copy files from them by using the cp command
cp /media/cdrom/file  /destination/file
eg
```
cp /media/cdrom/abc /home/tim/abc
```or
```
cp  /media/thumb/abc /home/tim/abc
```

---

### Post by prshah on 2008-11-17
> **richardmems said:**
> 
How can i access to the CD-ROM and thumb drives from Linux terminal or Console without using GUI file browser?

While you can use mount as "sudo", using "sudo" to mount the removable devices will allow only root access to the mounted filesystems.

A better alternative is to use [pmount]("apt://pmount"), which will mount the removable device, create the mount directory, and set relevant permissions, all automatically. Eg, if your usb device is sdd1, you can mount it with the simple command ```
pmount /dev/sdd1
``` (Note, do _not_ use sudo).

Alternately, you can manually fix permissions by giving suitable options to mount```
sudo mkdir /media/disk
sudo chown root:plugdev /media/disk
sudo mount /dev/sdd1 /mnt -o defaults,rw,umask=007,gid=46
```

Note that the options available vary from filesystem to filesystem.

---

