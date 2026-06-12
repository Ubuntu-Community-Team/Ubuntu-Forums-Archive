---
title: "Dual-Booted XP Pro &amp; Ubuntu 8.04, can't boot XP"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by Ryan Wolfe on 2008-06-29
Alright, here's the deal.. I've been scrounging around the whole day to find out what's wrong and fix it. I'm not the type to post on forums for help unless absolutely necessary. Now, I've familiarized myself with Ubuntu a bit, but I'm still a novice.

Here's what happened: My PC with XP Pro has a 500GB HDD. I shrunk the ~480GB XP Pro partition and made a 100GB partition to install Ubuntu 8.04 on. It installed fine and all is well, I'm loving Ubuntu. Now, I'm trying to get back to my XP Pro installation and it's not on the GRUB bootloader menu. So, I go into menu.lst and add a Windows XP Pro entry and I went through many partition IDs since I was unsure after my first try was a failure. But, here I am, all following attempts failing.

In my searches prior to this post, I saw that everyone requested menu.lst and sudo fdisk -l.. so, here they are.

**menu.lst**
```

## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

**sudo fdisk -l**
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
4 heads, 2 sectors/track, 122096646 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x0a431713

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       120813820   122096646     5131308   82  Linux swap / Solaris
/dev/sda3               2   120813819   483255272    5  Extended
/dev/sda5               2    26214401   104857599   83  Linux
/dev/sda6        26214402   120813819   378397671    7  HPFS/NTFS

Partition table entries are not in disk order

```

My XP installation is, apparently, on sda6. I've read that the HPFS/NTFS is a logical format which can't be booted from. Can someone verify if that's true? If so, I have no idea how because all I did was shrink the volume prior to installing Ubuntu 8.04.

Thanks for anyone's help ahead of time, it is greatly appreciated!

---

### Post by VMC on 2008-06-30
> **Ryan Wolfe said:**
> 
**menu.lst**
```

## ## End Default Options ##
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b29eacf8-c2a6-4e99-910e-f12949ede4c1 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		([COLOR="Red"]hd0,1[/COLOR])
savedefault
makeactive
chainloader	+1

```

**sudo fdisk -l**
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
4 heads, 2 sectors/track, 122096646 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x0a431713

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       120813820   122096646     5131308   82  Linux swap / Solaris
/dev/sda3               2   120813819   483255272    5  Extended
/dev/sda5               2    26214401   104857599   83  Linux
[COLOR="Red"]/dev/sda6        26214402   120813819   378397671    7  HPFS/NTFS
[/COLOR]
Partition table entries are not in disk order

```

My XP installation is, apparently, on sda6. I've read that the HPFS/NTFS is a logical format which can't be booted from. Can someone verify if that's true? If so, I have no idea how because all I did was shrink the volume prior to installing Ubuntu 8.04.

Thanks for anyone's help ahead of time, it is greatly appreciated!

I think something wrong. It appears from the fdisk output that you Windows partitions is on sda5 which in Grub speak is hd(0,4). Your menu.list shows hd(0,1).
Also Windows doesn't like it on any partition other than the first partition. So you need to "map" Windows to fool it thinking its still on the first partition.

But my question to you is what happened to /dev/sda1 ?

---

### Post by Ryan Wolfe on 2008-06-30
I have no idea what happened to sda1. The menu file is all the original file and I haven't messed with anything besides adding the Windows entry to the file. I haven't messed with partitions or anything since I installed Ubuntu.

I'm going to retry hd0,4 but I've tried it and others because I didn't know and it's just on hd0,1 since my last try. **--EDIT--** This didn't work. I got Error 12: Invalid device requested.

How would I "map" Windows to the first partition? And the weird thing is that it should be the first partition as far as my knowledge of it.. which is pretty large.

Thanks for the help

---

### Post by VMC on 2008-06-30
Something in this order , if your Windows is truly on /dev/sda6:

# Windows
title  Windows
map (hd0,0) (hd0,5)
map (hd0,5) (hd0,0)
rootnoverify (hd0,5)
chainloader +1

---

### Post by Ryan Wolfe on 2008-06-30
I tried that and all I didn't get any errors when trying to startup to that option.

But, it never got past "Starting up..."

Thanks for you very fast, diligent replies, too. This thing has been killing me all day.

---

### Post by Ryan Wolfe on 2008-06-30
No one else has any input on this? 

Can I atleast uninstall Ubuntu, reinstall XP in its place and recover my files from the old partition?

---

