---
title: "unable to change permission of /media/sda1"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by manu456 on 2007-03-26
Hi

I added a SATA drive to my computer, created new folders under /media, mounted the disks and added to fstab. 

The problem is that i did not change the permission of the folders to be read by all users. Now I am only able to access the mounted drives as root. If i try to change the permissions using chmod I get 

[COLOR="DarkRed"]chmod: changing permissions of `/media/sda1': Read-only file system[/COLOR]

The partitions that I am not able to access have are NTFS partitions...

---

### Post by taurus on 2007-03-26
Can you post your /etc/fstab here?

```
cat /etc/fstab
```

Otherwise, read this guide.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by manu456 on 2007-03-26
Here's my /etc/fstab file...

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=63abeecb-a65c-4f4a-94d9-816723530f7c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=001041ac-670a-49d4-902a-e5da484b67db none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#I've added the following lines
UUID=0220C3E220C3DB35	/media/sda1	ntfs	defaults	0	0
UUID=D040F81B40F80A4C	/media/sda2	ntfs	defaults	0	0
UUID=D6FC4740FC4719DF	/media/sda3	ntfs	defaults	0	0

```

---

### Post by pradeepadapa on 2007-03-26
hello, 

by default the ubuntu system mounts the drives which are of NTFS filesystem as read-only if u want to make them as write enabled, download nd install ntfs-3g driver from synaptic update or from automatix2, when that driver is installed, nd then reboot, u can then write to NTFS drives in any LINUX SYSTEM including UBUNTU....

---

### Post by taurus on 2007-03-26
Try something like these in /etc/fstab.

```

UUID=0220C3E220C3DB35	/media/sda1	ntfs   nls=utf8,umask=0222  0	0
UUID=D040F81B40F80A4C	/media/sda2	 ntfs	nls=utf8,umask=0222  0	 0
UUID=D6FC4740FC4719DF	/media/sda3	 ntfs	nls=utf8,umask=0222  0	 0

```
Then reboot.

---

### Post by manu456 on 2007-03-26
Thanks for your replies. It's not working.

I don't want write access to NTFS partitions, I just want to change folder permissions to allow read only access to all users. Right now only root has access.

---

### Post by taurus on 2007-03-26
umask=0222 will allow everybody to read the mount point.  Did you add that in (in /etc/fstab) and reboot?

---

### Post by manu456 on 2007-03-26
Thanks. It's working now :) 

Sorry I did not reboot the computer I had just done 
sudo mount -a

Thanks again and sorry for not following instructions properly.

---

