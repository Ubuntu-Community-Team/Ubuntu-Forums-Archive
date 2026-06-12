---
title: "Internal NTSF Drive Unmountable"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Bghmsh on 2008-02-07
Ubuntu runs like a champ on disk 1 , My seconday 250Gb drive seems to be unmountable , any command ideas Fdisk output supplied





Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11786    94671013+  83  Linux
/dev/hda2           11787       12161     3012187+   5  Extended
/dev/hda5           11787       12161     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf054f054

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdf5               2       30401   244187968+   7  HPFS/NTFS

---

### Post by logos34 on 2008-02-07
> **Bghmsh said:**
> Ubuntu runs like a champ on disk 1 , My seconday 250Gb drive seems to be unmountable , any command ideas Fdisk output supplied
which one--hdb or sdf?

Post the output from these commands:

mount

cat /etc/fstab

---

### Post by Bghmsh on 2008-02-08
bghmsh@bghmsh-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda1 on /media/Elements type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
nfsd on /proc/fs/nfsd type nfsd (rw)
/dev/sdc1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
bghmsh@bghmsh-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=55864ddb-aeec-40cc-8be6-928433140f1c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=bf81ed8b-72bd-4bf2-afcc-b63f54038bcf none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by logos34 on 2008-02-09
Since you didn't answer my question about which drive is the 'secondary' 250 gb, I'm guessing it's hdb1 you're referring to.

Follow[ this guide]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") to mount it.

---

