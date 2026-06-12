---
title: "Fresh Reinstall having problem with Maxor 80G drive"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2008-02-27
K had Ubuntu  running for a long time with a 120G WD drive and a 40G Maxor. Anyways my dad gave me his old box which is exact as mine except a 80G maxor hard drive that he also gave me. Any ways I swapped the ram to give me  512megs ram and replaced the old 40G Maxor with the the 80G maxor drive. Even then It had a slow boot hanging on about the first 10% of the prograss bar. I thought this had something to do with using the drive with the old install. Now after a fresh install I still have the same problem. Also with the 80G drive I could not use the live cd and even the alternative cd punched out errors but then was ok. I would really like to fix this problem and possibly do a bug fix for it.

 the output of fdisk -l is

```

Disk /dev/sda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd75bd75

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4106    32981413+   7  HPFS/NTFS
/dev/sda2            4107        9601    44138587+  83  Linux
/dev/sda3            9602        9732     1052257+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0f0f0f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   83  Linux


```

The output of mount is
```

/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sdb1 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)

```

---

### Post by deepclutch on 2008-02-27
did u checked bios?set the boot device priority to the drive which u want to boot first.
also,which drive are u trying to install Ubuntu?
make sure of the hdd jumper settings:
[http://www.tacktech.com/display.cfm?ttid=379](http://www.tacktech.com/display.cfm?ttid=379)

---

### Post by Omnios on 2008-02-27
Biosy is fine and its a normal set up. Only thing I can think of is that buntu is looking for somthing on boot and not finding it. This only happens within the say 5% of the boot slash bar so probably looking for he mounts.

---

