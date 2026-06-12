---
title: "Problem when upgrading from Feisty to Gutsy"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by foxtrot2000 on 2008-01-05
Hi,

I have just upgraded from Feisty to Gutsy and found that my home directory in /home seems to have disappeared so I am unable to login.

Has anyone else come across this problem? I don't suppose I can recover the data I had in /home??? Foolishly I hadn't made a backup of my home directory since my previous upgrades had been relatively painless.

Pls help!

Alex

---

### Post by taurus on 2008-01-05
Boot into recovery mode from GRUB menu and post the output of this command here.

```
ls -la /home
```

Do you have a separate /home partition?

---

### Post by foxtrot2000 on 2008-01-06
I can log in as root and when I do ls -la /home, I get:


drwxr-xr-x   2 root root 4096 2006-08-04 17:14 .
drwxr-xr-x 24 root root 4096 2008-01-06 12:08 .. 

Alex

---

### Post by taurus on 2008-01-06
How about 

```
fdisk -l
cat /etc/fstab
```

---

### Post by foxtrot2000 on 2008-01-06
root@almach:/home# fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            2433        2494      498015   82  Linux swap / Solaris
/dev/sda3            2495        4864    19037025   83  Linux



root@almach:/home# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=a17936f1-d481-4642-be7d-292dfdb7fa42 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda2 -- converted during upgrade to edgy
UUID=e21f5109-4d9b-4fff-ae26-2d83f2be6254 none swap sw 0 0
# /dev/hda1 -- converted during upgrade to edgy
UUID=f6a022cb-5172-4ae7-a2dd-0c26726855aa /home ext3 defaults 0 1
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2008-01-06
So you do have a separate partition for /home.  What's the output of this command then.  Just want to check the UUID for /dev/sda1.

```
ls -la /dev/disk/by-uuid
```

---

### Post by foxtrot2000 on 2008-01-06
root@almach:/home# ls -la /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 100 2008-01-06 20:20 .
drwxr-xr-x 6 root root 120 2008-01-06 20:20 ..
lrwxrwxrwx 1 root root  10 2008-01-06 20:20 a17936f1-d481-4642-be7d-292dfdb7fa42 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-01-06 20:20 e21f5109-4d9b-4fff-ae26-2d83f2be6254 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-01-06 20:20 f6a022cb-5172-4ae7-a2dd-0c26726855aa -> ../../sda1

---

### Post by taurus on 2008-01-06
What happens if you do

```
mount -t ext3 /dev/sda1 /home
ls -la /home
```

---

### Post by foxtrot2000 on 2008-01-06
root@almach:/# mount -t ext3 /dev/sda1 /home
mount: /dev/sda1 already mounted or /home busy

---

### Post by taurus on 2008-01-06
Can you post

```
df -h
```

---

### Post by foxtrot2000 on 2008-01-06
root@almach:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              18G   13G  5.1G  72% /
varrun                252M  104K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M   72K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   35M  218M  14% /lib/modules/2.6.22-14-386/volatile

---

### Post by taurus on 2008-01-06
Try something like

```
mkdir /media/sda1
mount -t ext3 /dev/sda1 /media/sda1
ls -la /media/sda1
```

---

### Post by foxtrot2000 on 2008-01-06
root@almach:/# mkdir /media/sda1
root@almach:/# mount -t ext3 /dev/sda1 /media/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy

---

### Post by taurus on 2008-01-06
There is a warning message about your /dev/sda1 from fdisk -l.

> 
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

Device Boot Start End Blocks Id System
/dev/sda1 1 2432 19535008+ 83 Linux
[COLOR="Red"]Partition 1 does not end on cylinder boundary.[/COLOR]
/dev/sda2 2433 2494 498015 82 Linux swap / Solaris
/dev/sda3 2495 4864 19037025 83 Linux


Did you somehow modify your partition table by any chance?

---

### Post by foxtrot2000 on 2008-01-06
I don't think I've changed anything related to my partitions. I don't know enough to do anything like that :-)

---

### Post by taurus on 2008-01-06
You probably need to use gparted and fix the first partition, /dev/sda1, before you can mount it.

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by foxtrot2000 on 2008-01-06
Thanks for all your help, taurus. I was pretty much panicking when my home directory couldn't be seen and your replies reassured me and helped calm me down :-)

I had a look around and other people were having similar problems mounting their partitions:

[http://ubuntuforums.org/showthread.php?p=3565991](http://ubuntuforums.org/showthread.php?p=3565991)

 I did the following and that seemed to have sorted it out:

apt-get install nfs-common
apt-get remove --purge evms

and then reboot.

Phew!

Alex

---

