---
title: "Grub Error 15"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by Niall Flinn on 2006-12-03
Hi Folks,

I've just attempted to install 6.10, so I've repartitioned one of the drives in my machine so I have a partition to install into and a swap partition, then installed as normal. However, on reboot, absolutely nothing happened, which I assumed was due to my MBR being destroyed when I partitioned the disk. I came across a tutorial on installing GRUB, so I did that, and sure enough, now when I reboot, I get a nice GRUB menu with a list of the different OSes in my machine - all good. I can boot into my old Ubuntu installation fine. Unfortunately, when I select the new 6.10 installation, I get the following error:

Error 15 - file not found.

Does anyone know what file this might refer to, and how I fix it? Is there something that doesn't get installed by default?

Thanks,

Niall

---

### Post by bulldog on 2006-12-03
Can you give us the outcome of ```
sudo fdisk -l (l as in like)
```
And your menu.lst as well please```
cat /boot/grub/menu.lst
```

---

### Post by Niall Flinn on 2006-12-03
Sure:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9351    75111876   83  Linux
/dev/sda2            9352        9729     3036285    5  Extended
/dev/sda5            9352        9729     3036253+  82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241   83  Linux

Disk /dev/hdc: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        4868    39102178+  83  Linux
/dev/hdc3           19502       20023     4192965   82  Linux swap / Solaris
/dev/hdc4            4869       19501   117539572+  83  Linux

Partition table entries are not in disk order

And:

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu, kernel 2.6.12-10-386 (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro single 
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu, kernel 2.6.12-9-386 (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash 
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/sda1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single 
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title           Ubuntu, memtest86+ (on /dev/sda1)
root            (hd2,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

/dev/hdc1 is the drive I've installed 6.10 into...

Thanks,

Niall

---

### Post by Sef on 2006-12-03
GRUB error 15 from the GRUB manual:

> 15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

---

### Post by bulldog on 2006-12-03
From which drive are you booting [with GRUB]
Because the numbering looks a little weird.
From fdisk I should understand sda is your boot disk but GRUB says it's (hd2)

It's critical to know which disk has GRUB cause this should be (hd0) the next disk is (hd1) and so on.
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0) <---
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```Change (hd1,0) into (hd0,0) and see if this will boot.
I think GRUB is on hdc which then should be (hd0)

---

### Post by Niall Flinn on 2006-12-03
> **Sef said:**
> GRUB error 15 from the GRUB manual:

Yep, I looked that up, but it's not terribly informative :(

Niall

---

### Post by Niall Flinn on 2006-12-03
> **bulldog said:**
> From which drive are you booting [with GRUB]
Because the numbering looks a little weird.
From fdisk I should understand sda is your boot disk but GRUB says it's (hd2)

It's critical to know which disk has GRUB cause this should be (hd0) the next disk is (hd1) and so on.
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0) <---
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```Change (hd1,0) into (hd0,0) and see if this will boot.
I think GRUB is on hdc which then should be (hd0)

sda contains my last Ubuntu installation - version 5.10.
hdc is the disk that I've installed 6.10 onto, and that I now want to boot from. 

When you say "which disk has GRUB", do you mean in the boot sector of the disk or in the ubuntu filesystem? I'm a little unclear as to how GRUB works and which bits of it should exist where...

Thanks for your help,

Niall

---

### Post by bulldog on 2006-12-03
GRUB let's you boot your OS's,but to do so it should be installed in the MBR of one of your disks.
Than you set this disk with GRUB as the master boot device so you can use it when you boot your computer.

Normally this disk with GRUB should be called (hd0)
If GRUB is installed on hdc,this would be (hd0)

Can you tell me which disk you're booting from,so you see the GRUB menu?
Try to boot from hdc and see if GRUB appears.

---

