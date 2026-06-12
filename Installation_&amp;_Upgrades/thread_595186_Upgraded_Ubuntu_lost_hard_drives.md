---
title: "Upgraded Ubuntu lost hard drives"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by tinoest on 2007-10-28
Hi,

I just upgraded to the latest Ubuntu from 7.04 and its lost some of my NTFS hard drives, at first I thought it was just them not being mounted but fstab does'nt even see them. I used to have them mounted at hdk1,hdi1,hdj1 and its still seen as that in /media just show's the folders as empty.. 

Typing ls /media shows:

tino@XP2600:~$ ls /media
cdrom  cdrom0  hdb1  hde1  hdf1  hdg1  hdh1  hdi1  hdj1  hdk1

mount shows:

tino@XP2600:~$ mount
/dev/hdb3 on / type reiserfs (rw,notail)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hdb1 on /media/hdb1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hde1 on /media/hde1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdf1 on /media/hdf1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdg1 on /media/hdg1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/hdh1 on /media/hdh1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)



ls /dev/disk/by-uuid/ -alh shows:

tino@XP2600:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 180 2007-10-28 20:00 .
drwxr-xr-x 6 root root 120 2007-10-28 20:00 ..
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 1545f989-3893-42fe-b7ac-e1c6732b5d12 -> ../../hdb2
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 520CB0200CB00151 -> ../../hdf1
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 766C95126C94CDED -> ../../hdh1
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 92D44168D4414FA1 -> ../../hde1
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 bff047bd-3148-4f7d-9dcd-7fc9bf04d3fe -> ../../hdb3
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 C4E83C2DE83C205A -> ../../hdg1
lrwxrwxrwx 1 root root  10 2007-10-28 20:00 D218B47318B45865 -> ../../hdb1

lastly sudo fdisk -l shows:

tino@XP2600:~$ sudo fdisk -l

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       57200    28828611    7  HPFS/NTFS
/dev/hdb2           57200       59113      963900   82  Linux swap / Solaris
Partition 2 does not end on cylinder boundary.
/dev/hdb3           59119       77545     9287208   83  Linux

Disk /dev/hde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55c9312e

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55c93131

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f522c1f

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdh: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4cba4cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1       19929   160079661    7  HPFS/NTFS

The hard drives where in there before I upgraded I did't think to make a copy of them , they are still seen in the bios so its not that im sure. Any help would be appreciated. 

thanks 

tino

---

