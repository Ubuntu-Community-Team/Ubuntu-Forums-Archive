---
title: "Cannot get access to my disk-drive under Gutsy Gibbon"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by li009 on 2007-10-28
The only way I could figure out to get access  to my disk-drive was to mount und umount it via the konsole. I absolutely did not get it to work at the Gutsy Gibbon Kubuntu Desktop! Using Feisty Fawn, however, this was easily done by typing "media:/" into the konqueror. But unfortunately with Gutsy Gibbon this does not seem to work anymore.

---

### Post by taurus on 2007-10-28
Why don't you add an entry in /etc/fstab for that harddrive/partition so it would mount automatically each time you boot Ubuntu.

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
mount
```

---

### Post by li009 on 2007-10-28
OK, here it is:

sudo fdisk -l:
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x73887388

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       19457   135315495    f  W95 Ext'd (LBA)
/dev/sda5            2612        5222    20972826    b  W95 FAT32
/dev/sda6            5223        7833    20972826   83  Linux
/dev/sda7            7834        8486     5245191   82  Linux swap / Solaris
/dev/sda8            8487       12403    31463271   83  Linux
/dev/sda9           12404       19457    56661223+  83  Linux

Disk /dev/sdb: 2029 MB, 2029518848 bytes
243 heads, 32 sectors/track, 509 cylinders
Units = cylinders of 7776 * 512 = 3981312 bytes
Disk identifier: 0xd5ca49d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         510     1981936    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(249, 242, 32) logical=(509, 184, 32)

cat /etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=bd7db977-7ad2-4db0-83b8-f77d071c2978 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda9
UUID=72e3c910-23a4-409b-ac50-0ebbbb8fa2df /data ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda8
UUID=b0e7333a-821a-48f1-80c0-a298e6cd06bb /home ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda1
UUID=786844096843C49A /media/sda1 ntfs defaults,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda5
UUID=C8B0-B5B0 /media/sda5 vfat defaults,utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
# /dev/sda7
UUID=bd063e60-8df0-427d-b3bb-d219fd7444b5 none swap sw 0 0
/dev/scd0 /media/cdrom0 auto user,atime,noauto,rw,dev,exec,suid 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0

mount:
> /dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda9 on /data type ext3 (rw)
/dev/sda8 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/sda5 type vfat (rw,utf8,umask=007,uid=0,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/USB DISK type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower)

---

### Post by taurus on 2007-10-28
Which harddrive are we talking here since everything is already mounted, including your second harddrive, /dev/sdb1--/media/USB DISK?

---

### Post by li009 on 2007-10-28
Not harddrive. Disk-drive!

---

### Post by mafsi on 2007-10-29
> **taurus said:**
> Why don't you add an entry in /etc/fstab for that harddrive/partition so it would mount automatically each time you boot Ubuntu.

Post the outputs of these commands from a terminal.

```
sudo fdisk -l
cat /etc/fstab
mount
```

hi, i will reply to this cause i dont want to open a new topic.
i'm very new to ubuntu & i need some help.

i run ubuntu in dual with XP. I installed and all is ok. I could mount / umount the other HDD (XP) from the command line & also from the GUI. My partitions were: hdc1 & hdc2 - swap.
I read on this forum that is better to have /home separated so i reinstalled ubuntu and made new partitions:

/boot = 300 MB
/        = 5 GB
/ home = 72 GB
/swap = 3 GB

When i boot in ubuntu my XP partitions are automatically mounted, BUT when i try to umount them i  run in errors = i don't have necessary permissions.

if i try :
```


sudo umount /media/sda1


```

is working

How can i grant permissions to mount drives to my user? Is it good to do this or should i execute this options via root?

Here are my HDD's

```

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000198c9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          38      305203+  83  Linux
/dev/hdc2            9353        9729     3028252+   5  Extended
/dev/hdc3              39         646     4883760   83  Linux
/dev/hdc4             647        9352    69930945   83  Linux
/dev/hdc5            9353        9729     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d794057

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       24321   159517417+   5  Extended
/dev/sda5            4463       10836    51199123+   7  HPFS/NTFS
/dev/sda6           10837       17210    51199123+   7  HPFS/NTFS
/dev/sda7           17211       24321    57119076    7  HPFS/NTFS


```

Thanks in advanced.

---

### Post by li009 on 2007-10-30
You have to edit the textfile
 
/etc/fstab
 
There you can specify, whether only root or also users can umount certain drives (don't ask me for exact details; I am still a newbie myself; a google-search should supply solution-details)

---

