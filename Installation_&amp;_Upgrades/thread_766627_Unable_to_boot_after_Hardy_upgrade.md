---
title: "Unable to boot after Hardy upgrade"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by lwpack on 2008-04-25
Hello. I just upgraded from Gutsy to Hardy, but upon rebooting, I get "Error 15, file not found."

Before upgrading, I had all my entries below the automagic line on the grub menu (I was having some issues so I didn't want the entries changed). However, after upgrading, these no longer boot (the linux ones anyway, I can still boot into windows).

I have a feeling I just need to edit my grub menu, but I'm not sure how. Can somebody help? Thanks.

Below I'm posting my grub menu, fdisk -l command, my fstab file, and my /boot folder.

## ## End Default Options ##


### END DEBIAN AUTOMAGIC KERNELS LIST ###

title 1. Ubuntu 7.10 Gutsy Gibbon
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
savedefault

title 2. Ubuntu 7.10 (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title 3. Ubuntu, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title 4. Windows Vista
root (hd0,2)
savedefault
makeactive
chainloader +1

title 5. Dell Diagnostic System Utility
root (hd0,0)
savedefault
makeactive
chainloader +1


lwpack@lwpack-pc:~$ sudo fdisk -l
Password:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 6 48163+ de Dell Utility
/dev/sda2 7 1312 10485760 7 HPFS/NTFS
/dev/sda3 * 1312 4499 25603305+ 7 HPFS/NTFS
/dev/sda4 4500 38913 276430455 5 Extended
/dev/sda5 4500 29995 204796588+ 7 HPFS/NTFS
/dev/sda6 * 29996 38548 68701941 83 Linux
/dev/sda7 38549 38913 2931831 82 Linux swap / Solaris
lwpack@lwpack-pc:~$



# /etc/fstab: static file system information.
#
# <device> <mount point> <file system> <options> <dump> <pass>

# proc
proc /proc proc defaults 0 0

# /dev/sda3 (Vista Partition)
# /dev/sda3 /media/vista ntfs-3g defaults,noauto,user,uid=1000,gid=1000,umask=0 0 0

# /dev/sda5 (NTFS Data Partition)
/dev/sda5 /media/ntfs ntfs-3g defaults,user,uid=1000,gid=1000,umask=0 0 0

# /dev/sda6 (Linux Root Partition)
/dev/sda6 / ext3 defaults,errors=remount-ro 0 1

# /dev/sda7 (Swap)
/dev/sda7 none swap sw 0 0

# /dev/scd0 (DVD +/- RW)
/dev/cdrom /media/cdrom0 udf,iso9660 user,noauto 0 0

# /dev/sdb1 (Thumbdrive)
/dev/sdb1 /media/thumbdrive vfat defaults,user,quiet,shortname=mixed,uid=1000,gid=1 000,umask=077,iocharset=utf8 0 0


lwpack@lwpack-pc:~$ ls /boot
grub initrd.img-2.6.17-11-generic.bak
initrd.img-2.6.17-10-generic.bak memtest86+.bin

---

### Post by Drone4four on 2008-04-25
This thread discusses how to fix a broken Grub using a LiveCD: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pumalite on 2008-04-25
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by lwpack on 2008-04-25
Neither of these options work (and I tried them).  The peculiar thing is that my /boot file says initrd.img-2.6.17-11-generic.bak even though hardy uses 2.6.25.x kernel.  I don't know what happened in the upgrade process.  Someone on linux forums said I had to do a fresh install, but I wanted to check to see if there were other options first.

---

