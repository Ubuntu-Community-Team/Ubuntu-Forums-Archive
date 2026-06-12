---
title: "can't write to 2d hdd, can see it"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by dagohill on 2007-04-24
[FONT="Courier New"]my second hard drive, a 20 g does show but i have no permissions to write to it.  (new 7.04 install over a 80 g hdd and a 20 g hdd. 

my fstab

 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e442d032-20dd-4ad9-9f48-5f88d66793db /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6818c92b-9504-4ee4-bb9f-a13d82da1093 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


[FONT="Courier New"]my df -h 
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G  2.7G   65G   4% /
varrun                760M  220K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  112K  760M   1% /proc/bus/usb
udev                  760M  112K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1             984M  763M  221M  78% /media/CORRNTIJUMP
/dev/hdb1              20G  2.2G   17G  12% /media/disk[/FONT]
[/FONT]

please help newbie to have the 2d hard drive be fully functional, ie, can read and write to it.

---

### Post by taurus on 2007-04-24
Is it (/dev/hdb1) ntfs, vfat, ext3, etc.?

```
sudo fdisk -l
```

---

### Post by dagohill on 2007-04-24
~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9331    74951226   83  Linux
/dev/hda2            9332        9733     3229065    5  Extended
/dev/hda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2482    19936633+  83  Linux

Disk /dev/sda: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)
$

---

### Post by dagohill on 2007-04-24
thanks, joe

---

### Post by taurus on 2007-04-24
Since /dev/hdb1 is ext3, you just need to change the ownership of it mount point, /media/disk, from root to your login name.  Then, you can write to it anytime you want.  Assuming your login name is **joe**, do

```
sudo chown -R **joe**:**joe** /media/disk
ls -la /media
```

---

### Post by dagohill on 2007-04-24
thank you Taurus. 
works fine. 
i now can write to it.

---

### Post by dagohill on 2007-04-24
lost the icon to the 2nd HD, the 20 gig. 
ls -la /media
total 44
drwxr-xr-x  7 root     root  4096 2007-04-24 21:55 .
drwxr-xr-x 21 root     root  4096 2007-04-22 21:26 ..
lrwxrwxrwx  1 root     root     6 2007-04-22 21:15 cdrom -> cdrom0
drwxr-xr-x  2 root     root  4096 2007-04-22 21:15 cdrom0
drwxr-xr-x  2 root     root  4096 2007-04-22 21:15 cdrom1
drwx------  9 correnti root 16384 1969-12-31 18:00 CORRNTIJUMP
drwx------  7 correnti root  4096 1969-12-31 18:00 DAD'S IPOD
lrwxrwxrwx  1 root     root     7 2007-04-22 21:15 floppy -> floppy0
drwxr-xr-x  2 root     root  4096 2007-04-22 21:15 floppy0
-rw-r--r--  1 root     root   317 2007-04-24 21:55 .hal-mtab
--wxr-x---  1 root     root     0 2007-04-15 06:56 .hal-mtab-lock

~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G  4.4G   63G   7% /
varrun                760M  216K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
procbususb            760M  140K  760M   1% /proc/bus/usb
udev                  760M  140K  760M   1% /dev
devshm                760M     0  760M   0% /dev/shm
lrm                   760M   33M  727M   5% /lib/modules/2.6.20-15-generic/volatile
/dev/sdb1             984M   65M  919M   7% /media/CORRNTIJUMP
/dev/sda2              38G   14G   24G  38% /media/DAD'S IPOD


$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9331    74951226   83  Linux
/dev/hda2            9332        9733     3229065    5  Extended
/dev/hda5            9332        9733     3229033+  82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2482    19936633+  83  Linux

Disk /dev/sda: 40.0 GB, 40000536064 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6        4863    39021885    b  W95 FAT32

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

thanks for the help, joe

---

