---
title: "Mounting a slave Hdd."
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by ItsGambit on 2007-12-08
So I am having problem with installing a Slave HDD. I am new here and am lost did a search and downloaded GParted..... formated the new 40GB hard drive and cant seem to find it on the machine. 

here is sudo fdisk -l 

> Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80ca80ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00049af9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4683    37616166   83  Linux

if some one could help me mount this that would be awesome....

thanks in advance,
ItsGambit

---

### Post by taurus on 2007-12-08
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /media/sdb1   ext3   defaults    0   1
```
Save it.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
```
Now, if you want to have a write permission to that partition, you need to change the ownership of /dev/sdb1 from root to your **username** (login name).

```
sudo chown -R **username**:**username** /media/sdb1
ls -la /media
```

---

### Post by ItsGambit on 2007-12-08
is there a way I can get an icon for the slave like i get one for my filesystem??

---

### Post by taurus on 2007-12-08
You mean an icon on your desktop.  You should have an icon on your desktop for that drive.  Maybe you need to reboot your machine.

---

### Post by sqrlking on 2007-12-09
Hi

I was having the same problem, and I came accross this thread.  Everything seems to go ok, but when I use mount -a, i get this:

```
mount -a
mount: special device /dev/hdb1 does not exist

```

the new hd is /dev/sdb1, i'm not sure what's going on.

---

### Post by taurus on 2007-12-09
If it's /dev/sdb1, then you have to use /dev/sdb1.  If it's /dev/hdb1, then use /dev/hdb1.  Otherwise, post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by sqrlking on 2007-12-09
I completed the instructions to mount the disk, I restarted, and the hard drive is usable.  But I still get the same thing when i mount -a.  I'm new, maybe I'm missing something

```
 sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003e828

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7109    57103011   83  Linux
/dev/sda2            7110        7297     1510110    5  Extended
/dev/sda5            7110        7297     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e8f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10011    80413326   83  Linux
```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f9da6f4f-88eb-4393-bc02-e5d7f14c13a1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=57c23272-68db-4483-b94d-8d99d631888a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdb1 /home ext3 defaults,errors=remount-rw 0 1
/dev/sdb1   /media/sdb1   ext3   defaults    0   1

```

---

### Post by taurus on 2007-12-09
> **sqrlking said:**
> I completed the instructions to mount the disk, I restarted, and the hard drive is usable.  But I still get the same thing when i mount -a.  I'm new, maybe I'm missing something


You already mount it from /etc/fstab so why do you have to run the "sudo mount -a" again?  Your second harddrive will be automatically mounted each time you boot Ubuntu since that is why you add an entry in /etc/fstab so you don't have to mount it by hand each time you want to use it.  So, forget about the "sudo mount -a" thing.

However, you don't have /dev/hdb1 so you need to put a # in front of that entry in /etc/fstab to comment it out.

```
#/dev/hdb1 /home ext3 defaults,errors=remount-rw 0 1
```

---

### Post by mackrackit on 2007-12-15
Hi  taurus,

I am setting up a  machine with  EDUBUNTU  for my six year old.

The instructions for two  hard drives was very helpful.  THANK YOU!!!

Now I would like to know how to change  the name  of hdb1 to MyStuff, as this drive is for storage.

Thank  you for your help.

Dave

---

### Post by taurus on 2007-12-15
> **mackrackit said:**
> Hi  taurus,

I am setting up a  machine with  EDUBUNTU  for my six year old.

The instructions for two  hard drives was very helpful.  THANK YOU!!!

Now I would like to know how to change  the name  of hdb1 to MyStuff, as this drive is for storage.

Thank  you for your help.

Dave

You mean you want to change the mount point from /media/hdb1 to /media/MyStuff?

Well, you can change the mount point in /etc/fstab if you have it mounted automatically, using /etc/fstab.  Don't forget to create the new mount point, /media/MyStuff or it won't mount the next time you boot.

---

### Post by mackrackit on 2007-12-15
Thank you, it worked.
Starting to understand more everyday.

"/dev/sdb"  Identifies it
" /media/sdb1"  Names it

---

### Post by j.miller565 on 2008-01-09
Thanks Taurus this helped me too

---

### Post by ROOP on 2008-02-15
sudo fdisk -l

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x039a039a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02500250

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    c  W95 FAT32 (LBA)
```


sudo gedit /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2f9c2b-78d0-4583-bbff-9b1685bf6d84 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2134d840-0d4e-43a9-b1cb-c0c8151d2376 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I can see the drive, but when i try to mount it always say mounted already or busy.

---

### Post by taurus on 2008-02-15
> **ROOP said:**
> sudo fdisk -l

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x039a039a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9824    78911248+  83  Linux
/dev/sda2            9825       10011     1502077+   5  Extended
/dev/sda5            9825       10011     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02500250

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    c  W95 FAT32 (LBA)
```


sudo gedit /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=de2f9c2b-78d0-4583-bbff-9b1685bf6d84 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=2134d840-0d4e-43a9-b1cb-c0c8151d2376 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I can see the drive, but when i try to mount it always say mounted already or busy.

What's the output of this command from a terminal?

```
df -h
```

---

### Post by ROOP on 2008-02-15
df -h in terminal

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              75G   62G  8.4G  89% /
varrun                379M  252K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M   92K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   35M  345M  10% /lib/modules/2.6.22-14-386/volatile
```

---

### Post by taurus on 2008-02-15
So you want to mount both /dev/sdb1 & /dev/sdd1.

```
sudo mkdir /media/sdb1 /media/sdd1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t vfat /dev/sdd1 /media/sdd1 -o umask=000
df -h
```

---

### Post by ROOP on 2008-02-15
Just the /dev/sdb1, The /dev/sdd1 is an external and is mounted and good.


```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
mount: /dev/sdb1 already mounted or /media/sdb1 busy
```



```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              75G   62G  8.4G  89% /
varrun                379M  252K  379M   1% /var/run
varlock               379M  4.0K  379M   1% /var/lock
udev                  379M   92K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   35M  345M  10% /lib/modules/2.6.22-14-386/volatile
```


Everything was fine on Feisty Fawn and the slave was mounted, but when I upgraded to Gutsy Gibbon, I can always see it, but wont let me mount always says already mounted or busy.

---

