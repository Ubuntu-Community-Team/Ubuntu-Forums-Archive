---
title: "How to attach a new hard drive"
date: 2007-09-15
forum: Installation &amp; Upgrades
---

### Post by jdbg on 2007-09-15
Hi,

I have relatively little experience with Ubuntu. I managed to put the 7.04 Server edition to a spare old PC I got to make it for a home server. Currently there is only one hard drive on which everything is installed.

I want to add another one, so that I can upload my shared folders there. How do I add a new drive?
I've heard that i should put it in the /etc/fstab, but how?

My current /etc/fstab is like this now:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4d628ac3-6e36-4891-a2a9-22d0fef58001 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=800d12b2-8103-4b8a-b6c4-a4863c80b7b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

What should I add? Btw the new drive is 20G IDE drive

10x in advance!

---

### Post by moonhk on 2007-09-15
My config file as below

moonhk@hex:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/backup     vfat iocharset=utf8,umask=000 0 0
#/dev/hdb1       /mnt/disk2      ext2  defaults 0 0
/dev/hdb1       /mnt/disk2       vfat umask=000 0 0


moonhk@hex:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             19086000   3097972  15018508  18% /
varrun                  257784       152    257632   1% /var/run
varlock                 257784         4    257780   1% /var/lock
udev                    257784       104    257680   1% /dev
devshm                  257784         0    257784   0% /dev/shm
/dev/hdb1             29288208   3177824  26110384  11% /mnt/disk2
moonhk@hex:~$

---

### Post by jdbg on 2007-09-15
A friend told me how to find the device and just share with everyone here:

```
sudo fdisk -l
```
with this I saw the name of the device

then I formated it with 
```
make mkfs.ext3 /dev/sdb1
```

Finally I added it to /etc/fstab
```
/dev/sdb1       /home/shares               ext3    defaults,errors=remount-ro 0       1
```

After that:
```
sudo man mount
```

```
mount -a
```

And then reboot and it now works! :)

---

