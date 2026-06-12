---
title: "Grub won't load after install on seperate harddisk."
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by tycho2 on 2006-11-12
Hi,

After running ubuntu on my laptop for 2 weeks i want to give it a shot on my desktop without interfering with my windows installation. So i decided to install edgy onto a seperate harddisk and use F8 on boot to boot from the ubuntu harddisk.

However, i've been trying this for a few days now and can't get it to work.
The hardware :

Asus p5b-deluxe wifi (P965 chipset)
sda : 250gb sata on onboard ICH8r controller. Raid data
sdb : 250gb sata on onboard ICH8r controller. Raid data
sdc : 250gb sata on onboard ICH8r controller. Raid data
sdd : 160gb sata on onboard ICH8r controller. Windows boot
sde : 160gb sata on Promise S150tx4 controller. The target for ubuntu.

I've also tried using a 10GB ide harddisk on the onboard jmicron controller. And putting the 160GB sata harddisk on the ICH8r instead of on the promise. But kept getting grub error 21 , or other errors.

I've gotten rid of the grub error 21 but now if i press F8 during boot and select the 160GB sata disk on the Promise controller to boot from it just loads windows, no grub menu, nothing.

The contents of /sde1/boot/grub/menu.lst is:
```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sde1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd4,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sde1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic

boot

title           Ubuntu, memtest86+
root            (hd4,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title           Microsoft Windows XP Professional
root            (hd3,0)
savedefault
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1


```

fdisk -lu gives the following output :
```

root@ubuntu:/home/ubuntu# fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001    7  HPFS/NTFS
/dev/sda2       488392065   976639544   244123740    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001    7  HPFS/NTFS
/dev/sdc2       488392065   976639544   244123740    7  HPFS/NTFS

Disk /dev/sdd: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sdd2       163846935   320143319    78148192+   f  W95 Ext'd (LBA)
/dev/sdd5       163846998   320143319    78148161    e  W95 FAT16 (LBA)

Disk /dev/sde: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63   308014244   154007091   83  Linux
/dev/sde2       308014245   320159384     6072570    5  Extended
/dev/sde5       308014308   320159384     6072538+  82  Linux swap / Solaris

```

Any suggestions on how to solve this?

---

