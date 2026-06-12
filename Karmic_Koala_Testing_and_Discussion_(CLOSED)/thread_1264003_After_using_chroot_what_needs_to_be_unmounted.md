---
title: "After using chroot what needs to be unmounted?"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-09-11
I'm using the following script but I'm having trouble using umount.


```
#!/bin/sh

## Directory /mnt/karmic already exists

sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

fi
```

After the script I'm using this with errors.
```
sudo umount /dev/sdb1
umount: /mnt/karmic: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

---

### Post by VMC on 2009-09-11
Here's someone with your same dilemma:
[http://www.unix.com/gentoo/66464-automating-chroot-mount-unmount.html](http://www.unix.com/gentoo/66464-automating-chroot-mount-unmount.html) 
Also go here [http://www.stsx.org/debian/pxedebian-chroot.html](http://www.stsx.org/debian/pxedebian-chroot.html)
and search for "Unmounting the chroot system"

---

### Post by philinux on 2009-09-11
I suspect I have to umount the stuff i mounted in reverse order?

---

### Post by philinux on 2009-09-11
Ok well rebooting does it but that is hardly stylish :P.

---

### Post by VMC on 2009-09-11
OK, I was successful in unmounting all the devices. Ctrl-d, got rid of the chroot bash,then in reverse order from bottom up unmount each one, from the SAME terminal I used to mount them.

---

### Post by VMC on 2009-09-11
I went through and captured the output:

```
	**$ sudo umount /dev/sda11**
umount: /mnt/disk: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

$ **mount**
...
/dev/sda11 on /mnt/disk type ext4 (rw)
/dev on /mnt/disk/dev type none (rw,bind)
/proc on /mnt/disk/proc type none (rw,bind)
/sys on /mnt/disk/sys type none (rw,bind)
/dev/pts on /mnt/disk/dev/pts type none (rw,bind)
	**$ sudo umount /mnt/disk/dev/pts**
**$ mount**
...
/dev/sda11 on /mnt/disk type ext4 (rw)
/dev on /mnt/disk/dev type none (rw,bind)
/proc on /mnt/disk/proc type none (rw,bind)
/sys on /mnt/disk/sys type none (rw,bind)
**  	$ sudo umount /mnt/disk/proc**
**$ mount**
...
/dev/sda11 on /mnt/disk type ext4 (rw)
/dev on /mnt/disk/dev type none (rw,bind)
	**$ sudo umount /mnt/disk/dev**
**$ mount**
...
/dev/sda11 on /mnt/disk type ext4 (rw)
	**$ sudo umount /mnt/dis**k
**$ mount**
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/vmc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=vmc)
/dev/sda5 on /media/DOWNLOADS type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```
I think you were trying also to unmount the wrong side.

---

### Post by philinux on 2009-09-11
Dunno. Chroot is absolutely essential in development. It needs a thorough howto.

---

### Post by xebian on 2009-09-12
> **philinux said:**
> I'm using the following script but I'm having trouble using umount.


```
#!/bin/sh

## Directory /mnt/karmic already exists

sudo mount /dev/sdb1 /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash

fi
```

After the script I'm using this with errors.
```
sudo umount /dev/sdb1
umount: /mnt/karmic: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
```

You have to un-mount first the points under it.  While /mnt/karmic/proc is mounted you can not un-mount /mnt/karmic.

BTW it's preferred to un-mount point not the dev.

---

### Post by philinux on 2009-09-12
Thanks guys will give that a go shortly.

---

