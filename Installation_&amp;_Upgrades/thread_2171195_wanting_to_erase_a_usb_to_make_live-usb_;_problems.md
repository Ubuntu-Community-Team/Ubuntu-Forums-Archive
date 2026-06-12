---
title: "wanting to erase a usb to make live-usb ; problems erasing it"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2013-08-29
a few weeks ago i thought to try and see what Opensuse looked like and installed   latest to my 8Gb usb using imagewriter which is the one recommended

now i want to erase usb to put 13.04 on it but it will not let me delete anything    and neither do unetbootin or imagewriter let me in

this is an area i know nothing about   but seems to be to do with mounting and permissions


all good advice welcome



ok   managed to get imagewriter to work and install 13.04     using sudo imagewriter    but still all files in my usb are now read only

what is in there


> sudo blkid[sudo] password for shan: 
/dev/sdg1: LABEL="Ubuntu-GNOME 13.04 amd64" TYPE="iso9660" 


tried to change ownership and this is what happens

> sudo chown shan /media/shan/'Ubuntu-GNOME 13.04 amd64'chown: changing ownership of ‘/media/shan/Ubuntu-GNOME 13.04 amd64’: Read-only file system







imagewriter seems to "lock" the usb      when  unetbootin has never done that


here is the problem


[ATTACH=CONFIG]245822[/ATTACH]

---

### Post by VMC on 2013-08-29
What's the output of *mount* for that device.

---

### Post by shantiq on 2013-08-29
hi VMC

is this what you mean?


>  /dev/sda1 on / type ext4 (rw,errors=remount-ro)proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/shan/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=shan)
[COLOR=#ff0000]/dev/sdb1 on /media/shan/Ubuntu-GNOME 13.04 amd64 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2)[/COLOR]





or


> mount '/dev/sdb1/media/shan/Ubuntu-GNOME 13.04 amd64'mount: can't find /dev/sdb1/media/shan/Ubuntu-GNOME 13.04 amd64 in /etc/fstab or /etc/mtab





and 


> umount '/dev/sdb1/media/shan/Ubuntu-GNOME 13.04 amd64'umount: /dev/sdb1/media/shan/Ubuntu-GNOME 13.04 amd64 is not mounted (according to mtab)





also this might be of help

> sudo blkid/dev/sda1: UUID="3caf2648-fd35-4dde-98b1-02332ab9ba3f" TYPE="ext4" 
/dev/sda5: UUID="80ba258b-21df-42f0-9490-a29e03dea23f" TYPE="swap" 
/dev/sdb1: LABEL="Ubuntu-GNOME 13.04 amd64" TYPE="iso9660" 
/dev/sdb2: SEC_TYPE="msdos" UUID="96BD-A183" TYPE="vfat"


both sdb are my usb in question

---

### Post by shantiq on 2013-08-29
also if useful



/etc/mtab


> /dev/sda1 / ext4 rw,errors=remount-ro 0 0proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfsd-fuse /run/user/shan/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=shan 0 0
/dev/sdb1 /media/shan/Ubuntu-GNOME\04013.04\040amd64 iso9660 ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks2 0 0


and

etc/fstab

> # /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3caf2648-fd35-4dde-98b1-02332ab9ba3f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80ba258b-21df-42f0-9490-a29e03dea23f none            swap    sw              0       0


/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0






[B]EDIT



[/B]

---

### Post by VMC on 2013-08-29
```
[COLOR=#FF0000]*/dev/sdb1 on /media/shan/Ubuntu-GNOME 13.04 amd64 type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8, mode=0400,dmode=0500,uhelper=udisks2)*[/COLOR]
```[COLOR=#FF0000][/COLOR]Your device is marked read only "*ro*"[COLOR=#FF0000][/COLOR]
```
dev/sdd1 on /media/vmc/USB 2.0 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,flush,uhelper=udisks2)
```

Also, the disk utility shows the device mounted when your trying to format. Unmount it first, create a partition then format.

---

### Post by shantiq on 2013-08-30
thanx VMC for you r  time here

i had got there in the meantime

> sudo umount   worked    then did something on gparted [cannot remember what]   to wipe all usb out

then


[B]
 by using disk utility

[/B]i have managed to reformat to** FAT32 **marked as solved

[IMG]http://s20.postimg.org/dy4bsm0t9/image.png[/IMG]

---

