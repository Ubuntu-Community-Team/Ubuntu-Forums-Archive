---
title: "2nd hard drive mounts at /boot"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by centralmtk on 2007-05-10
So i just installed a second hard drive which will just hold saved data. i created mount points for them in /etc/fstab and partitioned them with fdisk as regular Linux FS (83)

Now when i boot the computer, it mounts my new disk and then also mounts /boot on this disk as well.

here is my /etc/fstab and mount

/dev/mapper/mkfilesrv-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/sdb1 on /mnt/data type ext3 (rw,noexec,nosuid,nodev)
/dev/sdc1 on /mnt/home type ext3 (rw,noexec,nosuid,nodev)
/dev/sdc1 on /boot type ext3 (rw)

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/mkfilesrv-root /    ext3    defaults,errors=remount-ro 0       1
/dev/sdb1       /mnt/data       auto    rw,user 0       0
/dev/sdc1       /mnt/home       auto    rw,user 0       0
UUID=64f42e69-2c0f-498d-be90-51017366632f /boot           ext3    defaults        0       2
/dev/mapper/mkfilesrv-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


Can anyone tell me what im doing wrong? and/or how i can fix it?

---

