---
title: "installation of ubuntu on external usb hd, problem with grub, error 21"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by larne on 2008-01-28
Hello i am trying to move to ubuntu from windows but I am having problems. I installed ubuntu gutsy on an external USB harddrive. I remember that during installation my external USB HD was called "sda". I installed GRUB to "/dev/sda" during setup. After installation I changed the bootorder in BIOS to boot from the usb harddrive first. When I try to boot it hangs at GRUB stage 1_5, error 21. However I can boot up ubuntu with a systemrescuecd, but I would like to fix my GRUB. I googled alot but cant seem to fix it. Every time error 21. 

I did a fdisk -l as I have seen other people getting help being told to do so.

root@sysresccd /root % fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2793    22432768    7  HPFS/NTFS
/dev/sda2            2794       14593    94783500    5  Extended
/dev/sda5            2794       14593    94783468+   7  HPFS/NTFS

Disk /dev/sdb: 512 MB, 512483328 bytes
16 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         993      500355+   6  FAT16

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30409   244254368+   7  HPFS/NTFS
/dev/sdc2   *       30410       60044   238043137+  83  Linux
/dev/sdc3           60045       60801     6080602+   5  Extended
/dev/sdc5           60045       60801     6080571   82  Linux swap / Solaris

my /boot/grub/device.map looks like this:
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc

part of my /boot/grub/menu.lst looks like this:

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=bc3b72e2-aaf1-436c-acf7-78b657be07a5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)


## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc3b72e2-aaf1-436c-acf7-78b657be07a5 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bc3b72e2-aaf1-436c-acf7-78b657be07a5 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows Vista/Longhorn (loader)
root		(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1

One thing that surprises me is that sometimes the assigned names of the harddrives seem to change. I noticed it because when I was booting ubuntu using the rescuecd I wrote "rescuecd boothd=/dev/sdb2" It worked several times then suddenly it didnt work anymore. After a while I found out that the name had changed to sdc2. Can anybody help me please?

---

