---
title: "multiple distros/disks"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by rplantz on 2006-11-14
I want to install additional Linux distributions. Almost all the dual boot information on the web includes Windows. I do NOT want Windows on this machine.

I have two disks, which my bios lists as:
   Channel 1 is an IDE 80 GB
   Channel 2 is a SATA 160 GB

I have installed Edgy on the SATA disk and set my bios with the boot order:
   First -- Floppy
   Second -- CDROM
   Third -- Hard Disk
and boot priority
   1. Channel 2
   2. Channel 1

Since I know that my Edgy CD installs okay, I thought that I would also install Edgy on the IDE disk to make sure I am doing things correctly. When I get that to work, then I can replace it with another distro.

I tried, but when I attempt to boot the second Edgy installation (on the IDE disk), I get "Error 15: File not found."

My partitioning (from fdisk -l) is:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            9363        9727     2931862+  82  Linux swap / Solaris
/dev/sda3            1217        9362    65432745   83  Linux
/dev/sda4            9728       19457    78156225   a5  FreeBSD

Partition table entries are not in disk order

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        7649    61440561    5  Extended
/dev/hdc5               1        1147     9213214+  83  Linux
/dev/hdc6            1148        7394    50178996   83  Linux
/dev/hdc7            7395        7649     2048256   82  Linux swap / Solaris

```

The relevant (as far as I know) menu.lst entries on my SATA disk are, for my current Edgy installation on the SATA disk:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```
and for my new installation on the IDE disk:
```

title           Ubuntu, kernel 2.6.17-10-generic (on /dev/hdc1)
root            (hd1,4)
kernel          /boot/vmlinuz-2.6.17.10-generic root=/dev/hdc5 ro quiet splash 
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

The new Edgy installation on the IDE disk created a menu.lst file there that has the entry:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc5 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

I have tried changing "(hd0,4)" to "(hd1,4)" in the IDE menu.lst, but I still get the same error message.

Is my error that I need to have a primary partition one my IDE disk?

---

