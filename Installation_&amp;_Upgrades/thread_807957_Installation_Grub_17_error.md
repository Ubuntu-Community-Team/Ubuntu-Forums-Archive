---
title: "Installation Grub 17 error"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by petesmc on 2008-05-26
Hi,

Tried about 20 times last night to get Ubuntu (8.04) running but just could not. Here's the problem, i have 5 harddrives

1 = 74gb Windows
2 = 200gb
   a) Partition 1 = NTFS Storage
   b) Partition 2 = Ubuntu
3 = 1000gb NTFS Storage

4 = 320gb Ext3 Storage (Onboard raid controller - shouldn't be bootable i think)
5 = 1000gb NTFS Storage (Onboard raid controller - shouldn't be bootable i think)

The above the the order they are set to boot in, and also the same order as defined in the BIOS setup.

When installing ubuntu, it put grub onto hd0 which infact turned out to be a different drive (changed every installation). So now i have rogue grub installs every + MBRs on almost everydrive.

The last install i just messed with everything trying to get it to work but have given up and need your help.

I want the MBR onto hd0 (the 74gb drive) and the linux install is already on (hd1,1) - the 2nd partition on 200gb drive.

Here is my fdisk from live CD (i just did sudo fdisk -l). Ignore sdd1. It doesn't have linux installed, just formatted to ext3

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xbb3f87af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1     1938018   976761040+   7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006a42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9038    72597703+   7  HPFS/NTFS

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bc96bc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       21679   174136536    7  HPFS/NTFS
/dev/sdc2           21680       24321    21221865   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe8fc981

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   83  Linux

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x000abe2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1     1938018   976761040+   7  HPFS/NTFS

```

Here is my device.map. I did this:

```

sudo -s
mkdir /mnt/root
mount -t ext3 /dev/sdc2 /mnt/root
nano /mnt/root/boot/grub/device.map

```

```

(hd0)   /dev/sdb
(hd1)   /dev/sdc
(hd2)   /dev/sda
(hd3)   /dev/sdd
(hd4)   /dev/sde

```

Here is my menu.lst (the important bits i think)
```

## ## End Default Options ##

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=3d322783-4fed-4bd0-ba$
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=3d322783-4fed-4bd0-ba$
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

NOW, i just used Fixmbr to restore my windows MBR onto hd0 (74gb). There are probably grub mbrs lurking on other drives...would be nice to remove them, but most importantly, i need to update the MBR on hd0 so that it runs GRUB (which i want located on (hd1,1) (the 2nd partition of 200gb drive). How do i do this.

Hope i've provided enough information. I don't really know much about linux so if you need more info just tell me.

Regards,
Peter

EDIT: Forgot to mention, i was getting the error 17, when changing the boot order in the bios to set one of the other drives to boot first (to find where grub thought hd0 was) and then the error came up.

---

### Post by Pumalite on 2008-05-26
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by petesmc on 2008-05-26
I've been through that page many times and searched the forum plenty of times to. Everything i try ends up in a screwed up MBR, grub saying GRUB GRUB GRUB, error 17 and now...error 22.

Error 22 is can't find partition.

Following on from my first post, i did this

```

sudo -s
mkdir /mnt/root
mount -t ext3 /dev/sdc2 /mnt/root
grub --device-map=/mnt/root/boot/grub/device.map

grub> find /boot/grub/stage1
(hd1,1)
grub> root (hd1,1)
grub> setup (hd0)

```

Now, the correct harddrive has had it's MBR changed, but this error 22 means it can't find the correct partition. SO there is still some ordering problem going on.

---

### Post by meierfra. on 2008-05-26
I suggest to install grub to the MBR  of the 200g Ubuntu drive. If ubuntu is (hdx,1), then


sudo grub
root (hdx,1)
setup (hdx)
quit 

will work. (regardless of the  device map). You also need to change "root (hd1,1)" in menu.lst to "root (hd0,1)"

I realize that this is not want, but then at least you will know whether it is possible to boot Ubuntu at all. (If this does not work, it means that there is something else wrong which cannot be solved by messing with grub)

Alternatively, you might  remove all the drives  but the 74 gb and the 200 gb and see whether  you can boot ubuntu with you current grub-setup

---

