---
title: "new hard drive problem"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by Caesum on 2008-03-05
Bored of my graphics problems I thought I'd get my second hard drive working, I've tried to set it up as an encrypted file system, but I don't seem to be able to mount it, 

```

caesum@Caesum:~$ sudo lshw -C disk
[sudo] password for caesum:
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD-RW  DVR-215
       vendor: PIONEER
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.13
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: ST3500320AS
       vendor: ATA
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sda
       version: SD15
       serial: 9QM0VEES
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk
       description: SCSI Disk
       product: ST3500320AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: SD15
       serial: 9QM0Z3W1
       size: 465GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
caesum@Caesum:~$ sudo fdisk /dev/sdb

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eddde41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Command (m for help): q

caesum@Caesum:~$ sudo mke2fs -j /dev/sdb1
mke2fs 1.40.2 (12-Jul-2007)
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
caesum@Caesum:~$ sudo mount /dev/sdb1 /d2
mount: unknown filesystem type 'crypto_LUKS'
caesum@Caesum:~$ 


```

I've obviously gone wrong somewhere and then further messed things up. Anyway here is fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/Caesum-root
UUID=02af4b54-fcb3-43bd-aa06-bddcf5d455c5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=072f6564-f5be-4769-afd1-c57bd9289c33 /boot           ext3    defaults        0       2
# /dev/mapper/Caesum-swap_1
UUID=74890157-ea83-421b-b7e8-085b55839a77 none            swap    sw              0       0
# /dev/sdb1
UUID=50b8db1e-1002-44e4-987c-e557f9926e8f /d2             ext3    defaults 0 2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

and mtab:

```

/dev/mapper/Caesum-root / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/sda1 /boot ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,user=caesum 0 0

```

How can I sort this out?
Oh, and here is the problem on booting;

```

Log of fsck -C -R -A -a 
Wed Mar  5 16:31:53 2008

fsck 1.40.2 (12-Jul-2007)
/dev/sda1: clean, 32/62248 files, 33163/248976 blocks
fsck.ext3: Unable to resolve 'UUID=50b8db1e-1002-44e4-987c-e557f9926e8f'

fsck died with exit status 8

Wed Mar  5 16:31:54 2008
----------------

```

---

### Post by dstew on 2008-03-05
Not knowing anything about encrypted file systems, but something about logical volumes, it looks like you cannot mount /dev/sdb1 because it does not have a filesystem on it. Your mke2fs failed, and fsck wasn't happy because it could not find the volume corresponding to the UUID in your fstab.

My guess is that you should try to format it again. Maybe there is a special way to format an encrypted file system, other than mke2fs. Maybe you had to unmount it first, perhaps with a special command used by the encryption software. Anyway, after you get it formatted, you can do volume_id /dev/sdb1 to get the new UUID and change your fstab.

---

