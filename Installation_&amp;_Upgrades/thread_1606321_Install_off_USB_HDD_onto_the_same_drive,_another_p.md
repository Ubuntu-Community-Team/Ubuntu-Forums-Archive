---
title: "Install off USB HDD onto the same drive, another partition"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by jablan on 2010-10-26
I have created startup disk on my external USB HDD (on /dev/sdb1), I have been using it for some time, installed lots of software etc.

Now I would like to install it properly onto the same HDD. I have partitioned the rest of the drive (formatted /dev/sdb2 as ext4 for it), but when I try to install, the installer complains about needing to unmount /dev/cdrom (which is in fact a loopback image on /dev/sdb1), although I don't want to touch that partition (even unchecked grub option).

So, couple of questions:

1) How to install it onto the same USB HDD, different partition?
2) (optional) How to preserve everything I have installed?

```
$ mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000daddc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdb2            2551        5100    20482875   83  Linux
/dev/sdb3            5101        5227     1020127+  82  Linux swap / Solaris
/dev/sdb4            5228       19457   114302475    b  W95 FAT32


```

---

### Post by oldfred on 2010-10-26
I have always had my ISO files on one flash drive and installed to another. I also use grub to boot (loopmount) ISO files so I am not sure how persistence works. I do not think a new install to sdb2 will save any of your current settings.It 

Says you can install from same partition you boot from with workarounds.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

If persistence works like standard install, you will want to backup your /home as that has all your user settings and then backup system settings if you customized any from /etc. If you have installed a lot of applications you can also back those up.

 dpkg --get-selections > ubuntu-files
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by C.S.Cameron on 2010-10-26
Persistence files are saved in casper-rw.
You can access them as shown here:
[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

---

