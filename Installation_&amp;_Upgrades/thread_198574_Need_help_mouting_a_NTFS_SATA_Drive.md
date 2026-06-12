---
title: "Need help mouting a NTFS SATA Drive"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by ScotCop on 2006-06-17
As the title suggestions i need some help mouting my sata drive i managed to mount my windows one but i cant seem to get this one to show up and im not sure what device name it comes under.

---

### Post by cacharreo on 2006-06-17
Try using the disk manager. It's located on administration menu, or try from console:
***gksu disks-admin***
 
Cacharreo

---

### Post by bukwirm on 2006-06-17
'sudo fdisk -l' should list all your hard drives and partitions.

---

### Post by ScotCop on 2006-06-17
Cheer found it.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Only problem is when i go to mount it i get this error.

scotcop@area51:~$ sudo mkdir /media/test
scotcop@area51:~$ sudo mount /dev/sda /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: mount point /media/windows/ does not exist
scotcop@area51:~$ sudo mount /dev/sda /media/test/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda already mounted or /media/test/ busy
scotcop@area51:~$ sudo umount /media/test/
umount: /media/test/: not mounted
scotcop@area51:~$ sudo mount /dev/sda /media/test/ -t ntfs -o nls=utf8,umask=0222
mount: /dev/sda already mounted or /media/test/ busy
scotcop@area51:~$

Just not sure what im doing wrong i managed to get my windows IDE drive mounted tho.

---

### Post by cacharreo on 2006-06-17
I think it is because you are trying to write into the ntfs drive. It's not supported by linux. Ntfs read only is supported

---

