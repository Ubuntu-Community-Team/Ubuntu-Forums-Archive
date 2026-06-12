---
title: "Kubuntu Feisty desktop device icons disappeared since update from Edgy"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by emil_p8 on 2007-04-03
Well, all my hard disk device icons do not show on my desktop anymore, even if they are auto mounted at startup. However, if i mount a hd by hand, it shows up, and cdroms & usb keys get automounted and shown. BTW, all my /dev/hdX became /dev/sdX. Here's my feisty fstab, a bit messy since i have it from dapper on, and the logic of this uuid thingy introduced by edgy made it a quite unfriendly place. So, any help?

[I]#  /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=19646148-acf6-4c82-80af-44fcf9bc1c8d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=A8CC5A3FCC5A07C8 /media/hda1 ntfs defaults,ro,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=36D86D39D86CF90F /media/hda5 ntfs defaults,ro,nls=utf8,umask=007,gid=46 0 1
# automatic entry disabled by me
#/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6 -- converted during upgrade to edgy
UUID=af4e2262-53fe-4e53-9905-f1c49aa0858d none swap sw 0 0
# Win98 VFAT 2.5 Gb
/dev/hdb1       /media/hdb1     vfat    user,noauto,iocharset=utf8,umask=007,gid=46     0       0
# automatic entry disabled by me
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
[/I]

And this is my pre-uuid fstab (dapper)

[I]GNU nano 2.0.2                            File: /etc/fstab.pre-uuid                                                               

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,ro,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,ro,nls=utf8,umask=007,gid=46 0       1
# automatic entry disabled by me
#/dev/sda1       /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda6       none            swap    sw              0       0
# Win98 VFAT 2.5 Gb
/dev/hdb1       /media/hdb1     vfat    user,noauto,iocharset=utf8,umask=007,gid=46     0       0
# automatic entry disabled by me
#/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

[/I]


Here's mount output

creaphot@creaphot:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-13-generic/volatile type tmpfs (rw)
/dev/mapper/sda1 on /media/hda1 type ntfs (ro,nls=utf8,umask=007,gid=46)
/dev/mapper/sda5 on /media/hda5 type ntfs (ro,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/hdb1 type vfat (rw)

---

