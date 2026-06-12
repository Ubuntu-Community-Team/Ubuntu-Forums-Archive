---
title: "Can't mount sata drive"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by ... on 2006-07-10
Ok, I just got a pair of new sata barricudas and I am trying to get them working happily...  I started out trying to use mdadm and making a raid out of them, but after a day or so I got a 'device dissapeared' error and the array was gone.  So I gave up with the raid and decided to mount the drives on my own.  So I created a new partition table with a single partition, and formatted fat32, and mounted them (which worked) and added an extry in fstab.  Then I rebooted.  The drives did not mount on their own.  Then I tried 
sudo mount -t vfat /dev/sda1 /test
and was met with
mount: /dev/sda1 already mounted or /test busy
So then I tried 
sudo umount /dev/sda1
and was met with 
umount: /dev/sda1: not mounted

And I know that /test is not busy since I had just made it...

I should point out that I have done a complete removal of mdadm, and the only raid stuff left is the lvm support stuff that came with ubuntu...  I am running v6 (upgraded from v5)

So does anyone know why I can't mount the drive?

THANKS!

---

### Post by taurus on 2006-07-10
A couple of things.  What does your /etc/fstab look like and what is the output of this command, from a terminal?
```

more /etc/fstab
df -h

```

---

### Post by ... on 2006-07-10
fstab: (I commented out the lines for the sata drives since I thought they were being mounted wrong at startup)
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /data/primary   vfat    uid=1000,gid=100,umask=0000      0       0
#/dev/hdb1       /data/windows   ntfs    iocharset=utf8,umask=000   0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1       /data/secondary vfat    uid=1000,gid=100,umask=1000      0       0
#/dev/sdb1       /data/backup    vfat    uid=1000,gid=100,umask=1000      0       0
/dev/hdb2       /data/maxtor    vfat    uid=1000,gid=100,umask=1000  0  0
```           

output of that command:
```
peter@Dell:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /data/primary   vfat    uid=1000,gid=100,umask=0000      0
 0
#/dev/hdb1       /data/windows   ntfs    iocharset=utf8,umask=000   0       0
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
#/dev/sda1       /data/secondary vfat    uid=1000,gid=100,umask=1000      0
  0
#/dev/sdb1       /data/backup    vfat    uid=1000,gid=100,umask=1000      0
  0
/dev/hdb2       /data/maxtor    vfat    uid=1000,gid=100,umask=1000      0
 0
peter@Dell:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             8.3G  4.0G  3.9G  52% /
varrun                506M  132K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  184K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-25-386/volatile
/dev/hda3              28G  2.1G   26G   8% /data/primary
/dev/hdb2              95G   89G  6.7G  94% /data/maxtor
/dev/hdb1              20G  3.6G   17G  18% /data/windows
/data/maxtor/ftp       95G   89G  6.7G  94% /data/primary/FTP-shared/peter/data
/data/maxtor/ftp       95G   89G  6.7G  94% /data/primary/FTP-shared/mike/data
/data/maxtor/ftp       95G   89G  6.7G  94% /data/primary/FTP-shared/erik/data
```

I realise they are pretty ugly, primarily from trying to get e decent multiuser proftpd setup working](*,)  IMHO pureftpd is miles better


Thanks!

---

