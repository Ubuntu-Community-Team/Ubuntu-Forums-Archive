---
title: "Cannot mount any drive"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by sadalmelik57 on 2008-03-05
I was a solid Ubuntu user until November 2007 when I upgraded to Gutsy on my main PC. The upgrade failed at some point near the end - I think the sticking point was the time zone data, which I was able to find a solution for and fix.  However after that point I could not see or mount any of my hard drive partitions.  GParted can see the space, but I cannot access any of it.  I thought I could figure this out on my own but I've been unable to solve it and I resorted to using another non-linux OS.  ](*,)](*,)](*,):mad:

My dual-boot PC has a 40 gb NTFS hard drive for XP Windows (in Windows known as the C drive or in GParted it is /dev/sdb), and a 160 gb hard drive (AKA /dev/sda) partitioned into 75 mb FAT32 "D Drive" or /dev/sda3, 50 mb FAT32 ("F Drive" or /dev/sda1), 25mb EXT3 Linux and Boot (known as /dev/sda2), and 1.5 gb Swap (known as /dev/sda4).  In addition I have an external "MyBook" hard drive of 465gb FAT32 (known to GParted as /dev/sdc).  I can no longer see any of the hard drive space other than the file system /dev/sda2.  Computer shows MyBook but clicking on it results in an error message that the drive cannot be mounted, and the details say it is either in use or it is already mounted.  I've tried umount and mount to no avail.

Here is my current FSTAB:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                        0  0  
# /dev/hda2 -- converted during upgrade to edgy
UUID=d164847e-1464-4bef-ba81-c4d30a4df37e  /               ext3         defaults,errors=remount-ro      0  1  
# /dev/hda1 -- converted during upgrade to edgy
UUID=4543-B915                             /media/hda1     vfat         defaults,utf8,umask=007,gid=46  0  1  
# /dev/hda3 -- converted during upgrade to edgy
UUID=4507-341B                             /media/hda3     vfat         defaults,utf8,umask=007,gid=46  0  1  
# /dev/hda4 -- converted during upgrade to edgy
UUID=7681c584-ab42-44dd-8d23-1efaa912914e  none            swap         sw                              0  0  
/dev/cdrom                                 /media/cdrom0   udf,iso9660  user,noauto                     0  0  


Any assistance would be greatly appreciated.  I'd like to get back to daily Ubuntu use.

---

### Post by taurus on 2008-03-05
Also post

```
sudo fdisk -l
df -h
```

---

### Post by sadalmelik57 on 2008-03-05
:~$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7444292

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           12749       19261    52315672+   b  W95 FAT32
/dev/sda2   *        9562       12748    25599577+  83  Linux
/dev/sda3               1        9561    76798701    b  W95 FAT32
/dev/sda4           19262       19457     1574370   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           5       40131   de  Dell Utility
/dev/sdb2   *           6        4862    39013852+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G   18G  5.4G  77% /
varrun                633M  216K  633M   1% /var/run
varlock               633M  4.0K  633M   1% /var/lock
udev                  633M  136K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   35M  599M   6% /lib/modules/2.6.22-14-386/volatile
:~$ 


Thanks for looking!

---

### Post by taurus on 2008-03-05
I suppose you want to mount /dev/sda1, /dev/sdb2, and /dev/sdc1.

```
sudo mkdir /media/sda1 /media/sdb2 /media/sdc1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
sudo mount -t ntfs /dev/sdb2 /media/sdb2
df -h
```

---

### Post by sadalmelik57 on 2008-03-05
:~$ sudo mkdir /media/sda1 /media/sdb2 /media/sdc1
mkdir: cannot create directory `/media/sda1': File exists
mkdir: cannot create directory `/media/sdb2': File exists
mkdir: cannot create directory `/media/sdc1': File exists
:~$ sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
mount: /dev/sda1 already mounted or /media/sda1 busy
:~$ sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
mount: /dev/sdc1 already mounted or /media/sdc1 busy
:~$ sudo mount -t ntfs /dev/sdb2 /media/sdb2
fuse: mount failed: Device or resource busy
:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              25G   18G  5.4G  77% /
varrun                633M  216K  633M   1% /var/run
varlock               633M  4.0K  633M   1% /var/lock
udev                  633M  136K  633M   1% /dev
devshm                633M     0  633M   0% /dev/shm
lrm                   633M   35M  599M   6% /lib/modules/2.6.22-14-386/volatile

---

### Post by sadalmelik57 on 2008-03-05
That is the same problem I keep running into.  The response is that the drive is already mounted or busy.  It seems to be mounted, but I still cannot access it.:(

---

