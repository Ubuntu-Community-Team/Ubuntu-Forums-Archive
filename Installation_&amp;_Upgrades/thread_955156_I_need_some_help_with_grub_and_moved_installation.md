---
title: "I need some help with grub and moved installation"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by sgtstadanko on 2008-10-21
Hey All,

I decided to blow away my Vista installation and am having some boot issues with grub. I have 2 drives.  Primary is 80gb (where vista lived) , Secondary 250 GB (ubuntu 8.04).  I wanted to move the ubuntu installation to the primary so I could use the secondary as storage.  I blew away the first drive with gparted, created and formatted an ext3 partition on /dev/sda1.  

I then booted from a livecd and mount both disk1 (sda1) and disk2 (sdb5).  I did a:

cp -ax /* /mnt/disk2 - from the disk2 directory (the ubuntu installation)
edit /etc/fstab and changed sdb5 to sda1 
edit /boot/grub/menu.lst to add /dev/sda1 as a Moved Ubuntu entry
run update-grub

I verified that all the files copied over to the new partition and that the changes I wrote to fstab where in the correct directory.


However whenever I boot selecting the new grub menu item it always boots and mount the old sdb5 installation.

Here are the contents of my menu.lst and fstab.  Maybe someone can see something I missed.

```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=90d22947-b15e-4328-806f-e7bb810224b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Moved Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=90d22947-b15e-4328-806f-e7bb810224b0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```



/etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=90d22947-b15e-4328-806f-e7bb810224b0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
/dev/sdb1	/mnt/store	ntfs	defaults 0 0 
UUID=02865f16-9474-4e60-a362-1ab858fb1a0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by caljohnsmith on 2008-10-22
> **sgtstadanko said:**
> 
```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]90d22947-b15e-4328-806f-e7bb810224b0[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Moved Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=[COLOR="Red"]90d22947-b15e-4328-806f-e7bb810224b0[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```



/etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=[COLOR="Red"]90d22947-b15e-4328-806f-e7bb810224b0[/COLOR] /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
/dev/sdb1	/mnt/store	ntfs	defaults 0 0 
UUID=02865f16-9474-4e60-a362-1ab858fb1a0b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Above you are using the same UUID for your Ubuntu install on (hd1,4) or sdb5 and also (hd0,0) or sda1. How about posting:
```
sudo blkid -c /dev/null
```
So we can see what your correct UUIDs are. That may be all you need to fix in your menu.lst and possibly fstab, depending on which UUID is correct. :)

---

### Post by sgtstadanko on 2008-10-22
that was it.  i had changed the block id in the menu.lst at one point but not fstab.

all is well now.

thanks!

---

