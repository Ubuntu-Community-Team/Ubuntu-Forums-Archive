---
title: "Logical Volume - Mounted in Read-Only mode!"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Aikon- on 2006-08-30
Help!

Okay, this is a little more serious than the previous problem.

When I mount the logical volume lvdata as I indicated above, its getting mounted in read-only mode.. I cannot write to this volume!



Output of vgdisplay:
```
  --- Volume group ---
  VG Name               lvga
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               0
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               298.09 GB
  PE Size               4.00 MB
  Total PE              76311
  Alloc PE / Size       76311 / 298.09 GB
  Free  PE / Size       0 / 0
  VG UUID               qqcsh2-BJ7p-1h2M-zp9J-Caq1-IZKL-GF3msO

```

Output of lvdisplay:
```
  --- Logical volume ---
  LV Name                /dev/lvga/lvhome
  VG Name                lvga
  LV UUID                yGT7Vm-2qdK-Nz1w-emCf-RZJk-lrvm-W5G1eC
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                50.00 GB
  Current LE             12800
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/lvga/lvdata
  VG Name                lvga
  LV UUID                Yqn53K-Ruk1-WE4z-3x3e-2hAg-rgMy-5OTViQ
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                248.09 GB
  Current LE             63511
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

```

Output of   ls -l /media:
```
total 44
lrwxrwxrwx 1 root root        6 2006-07-26 14:21 cdrom -> cdrom0
drwxr-xr-x 2 root root     4096 2006-07-26 14:21 cdrom0
drwxr-xr-x 2 root root     4096 2006-08-30 06:56 cdrom-1
drwxr-xr-x 2 root root     4096 2006-08-30 06:56 dvdrecorder
drwxrwxrwx 2 root root     4096 2006-08-30 18:26 file-03
dr-xr-x--- 1 root plugdev 12288 2006-08-30 07:03 pet-file-02
dr-xr-x--- 1 root plugdev 16384 2006-08-30 07:03 pet-win-01

```


My /etc/fstab file:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/lvga/lvdata        /media/file-03  ext3    defaults,errors=remount-ro      0       1
/dev/sda1       /media/pet-file-02 ntfs defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb1       /media/pet-win-01 ntfs  defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by kewldude606 on 2006-08-30
Its because the owner is root.

Are you mounting a FAT32 partition?  If so, the fstab should look like this:
/dev/sda1       /mnt/big/       vfat    **rw,user,umask=0** 0       0

(the important part is the 4th column)

As a quick fix, you should be able to delete/write using sudo.

---

### Post by Aikon- on 2006-08-30
> **kewldude606 said:**
> Its because the owner is root.

Are you mounting a FAT32 partition?  If so, the fstab should look like this:
/dev/sda1       /mnt/big/       vfat    **rw,user,umask=0** 0       0

(the important part is the 4th column)

As a quick fix, you should be able to delete/write using sudo.

No, this is an ext3 partition (for which, I believe, the umask option means nothing?)

---

### Post by Aikon- on 2006-08-30
For clarification:
This is a central media storage location, and should be visible / writeable by all users. The logical volume is formatted with ext3 and is listed as the 3rd entry in the /etc/fstab file I pasted before.

---

### Post by m.musashi on 2006-08-31
Interesting problem. I can't claim to be any great source of knowledge on this type of issue, but I have a second hd formated for linux and my fstab looks slightly different. What happens if the line that reads
```
/dev/lvga/lvdata        /media/file-03  ext3    defaults,errors=remount-ro      0       1
```
looked like
```
/dev/lvga/lvdata        /media/file-03 ext3 defaults 0 0
```
In my case it's a reiserfs volume and reads
```
/dev/hdc7	/media/suse	reiserfs defaults 0 0
```
but I wonder if it wouldn't work the same. Just a thought.

---

### Post by Aikon- on 2006-08-31
With the help of [Mssever]("http://ubuntuforums.org/member.php?u=126210") I was able to resolve the problem. The process involved something along these lines:

```
sudo chmod 777 /media/file-03
```

IMO this should have been enough, but I suppose I needed to "force" Ubuntu to notice the changes, so:

```
sudo mkdir /media/file-03/test
sudo chmod 777 /media/file-03/test
touch /media/file-03/test/bogus.file
```

These commands were successful, and it did indeed place the folder and file where I expected them, to which I could read/write through Nautilus. At this point, the existing lost+found and test file in /media/file-03 added the "locked" emblem to themselves and I still couldn't create a new folder or file in /media/file-03. So:

```
sudo chmod /media/file-03/lost+found /media/file-03/test.txt
```

After this I was able to read/write to all folders under /media/file-03 as well as create new files/folders at the "root" of this drive.

Thanks for all your help guys! (and gals ;)

---

