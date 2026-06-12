---
title: "System Hangs during Quiet Splash"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Kalimar on 2007-06-04
My last system update has caused my system to hand during the quiet splash. After reading and posting on another thread I think we have come to the conclusion the problem is probably in the fstab file and relates to mounting  EVMS. Of course, I'm not sure at all about any of this and appreciate and help you might provide.  I've included the output of the following files/commands: menu.lst, FSTAB, BLKID, and FDISK -l 
I hope it doesn't make the post too long :s

What follows is the output of the following files/commands
/media/ubuntu/boot/grub/menu.lst
/media/ubuntu/etc/fstab
sudo blkid
sudo fdisk -l

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-386
savedefault

title		Ubuntu, kernel 2.6.20-16-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro single
initrd		/boot/initrd.img-2.6.20-16-386

title		Ubuntu, kernel 2.6.20-15-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro single
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro single
initrd		/boot/initrd.img-2.6.15-28-386

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 ro single
initrd		/boot/initrd.img-2.6.12-9-386

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=294c82a0-3ef7-40c4-917b-6c213ed85916 /  ext3  defaults,errors=remount-ro   0       1
# /dev/hda5
UUID=a2bfc36b-766a-46ce-9998-3bcb1400d748 none            swap    sw              0       0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

BLKID

/dev/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/cloop0: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/mapper/casper-snapshot: UUID="cc2eea34-0517-4918-aabe-383ac253aad6" TYPE="ext2"
/dev/evms/hda1: LABEL="/" UUID="294c82a0-3ef7-40c4-917b-6c213ed85916" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="a2bfc36b-766a-46ce-9998-3bcb1400d748" TYPE="swap"
/dev/sda1: UUID="E8FE-A636" SEC_TYPE="msdos" TYPE="vfat"


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris

---

