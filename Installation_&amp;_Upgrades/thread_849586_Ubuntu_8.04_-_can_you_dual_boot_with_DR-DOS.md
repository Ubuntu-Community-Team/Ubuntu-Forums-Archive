---
title: "Ubuntu 8.04 - can you dual boot with DR-DOS?"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by JohnLauritsen on 2008-07-04
For two years I've used Dapper Drake 6.06.  Using the alternate install disk, I put GRUB on a floppy.  Without the floppy I get a dual boot: Windows 98SE and DR-DOS.  With the floppy, I get Ubuntu.  Thus, I have three different , completely independent operating systems.  A bit awkward, but it works fine.

I have the alternate install disk for Hardy Heron 8.04.

Now I want to ditch Windows completely on a new laptop.  Without excessive tweaking, is it possible to get a dual boot: Ubuntu 8.04 and DR-DOS (preferably) or another non-Microsoft DOS?  If it is possible, what do I do?

JL

---

### Post by zzatz on 2008-07-04
You can install GRUB on a floppy, as you are doing now. Or you can install it on the Master Boot Record of the hard disk. You can also install GRUB onto a partition, so that it is called from some other boot loader.

The standard way to install DR-DOS and Ubuntu would be to install DOS first, on the first partition. If your whole hard drive is /dev/sda, that would be /dev/sda1. DR-DOS will install its own boot loader on the Master Boot Record of /dev/sda.

Later, when you install Ubuntu onto /dev/sda2, the installer will put GRUB on the Master Boot Record. But before it does that, it will move the the DOS boot loader, so that it can call it with a technique called chainloading.

Each drive has a Master Boot Record. Each partition MAY have a boot record. And GRUB can use boot records saved as files in /boot.

Your /boot/grub/menu.lst file would contain something like this:

```
#
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.24-19-generic root=/dev/mapper/vglinux-root ro quiet splash
initrd		/initrd.img-2.6.24-19-generic
#
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

Note that Linux counts partitions starting from 1, and GRUB counts starting from 0. GRUB's (hd0, 1) is /dev/sda2 in Linux.

Your setup is easy. For more complex setups, learn the grub-install command. Every Microsoft OS takes over the MBR, so if you install Windows later, you will need to reinstall GRUB. After booting from CD...

---

