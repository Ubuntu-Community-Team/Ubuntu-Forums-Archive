---
title: "help booting Acer Switch 10 directly to Ubuntu"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by miatawnt2b on 2015-05-06
Hello,

I am trying to get my Acer Switch10 to boot directly into ubuntu and am having a hard go of things. This is a baytrail machine that will only boot a 32bit EFI.
I blew away the windows partition, and installed 64bit 15.04 using a USB stick that had the 32bit efi bootloader. I was able to get teh machine to boot ubuntu from its internal ssd using the USB stick to get to a grub menu, then entering the following
```

linux (hd1,gpt4)/vmlinuz-3.19.0-16-generic root=/dev/mmcblk0p5
initrd (hd1,gpt4)/initrd.img-3.19.0-16-generic
boot

```

works great. So I've tried to install 32bit grub, but no luck getting that to work. So I copied the bootia32.efi from my usb stick into /boot/efi/EFI/Boot

the machine now drops me to the grub prompt without needing the usb stick. So far so good, but now I'm stuck. I still need to manually enter the kernel initrd and root info into grub to get Ubuntu to boot... now with the following (note hd1 is not hd0 without the usb inserted)

```

linux (hd0,gpt4)/vmlinuz-3.19.0-16-generic root=/dev/mmcblk0p5
initrd (hd0,gpt4)/initrd.img-3.19.0-16-generic
boot

```

So how can I get grub to boot automatically at this point?

```

root@switch:/# fdisl -l
No command 'fdisl' found, did you mean:
 Command 'fdisk' from package 'util-linux' (main)
 Command 'fdisk' from package 'gnu-fdisk' (universe)
fdisl: command not found
root@switch:/# fdisk -l

Disk /dev/mmcblk0: 29.1 GiB, 31272730624 bytes, 61079552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 5D8553B1-F56A-45E8-A36E-C50E855C3F96

Device            Start      End  Sectors  Size Type
/dev/mmcblk0p1     2048   206847   204800  100M EFI System
/dev/mmcblk0p2   206848   468991   262144  128M Microsoft reserved
/dev/mmcblk0p3 53080064 61077503  7997440  3.8G Linux swap
/dev/mmcblk0p4   468992  1468415   999424  488M Linux filesystem
/dev/mmcblk0p5  1468416 53080063 51611648 24.6G Linux filesystem

Partition table entries are not in disk order.
 
Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
The backup GPT table is corrupt, but the primary appears OK, so that will be used.

Disk /dev/mmcblk1: 30.5 GiB, 32715571200 bytes, 63897600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2163B331-5DD9-4235-8C68-39E43DF925DF

Device         Start      End  Sectors  Size Type
/dev/mmcblk1p1  2048 63895551 63893504 30.5G Microsoft basic data

root@switch:/# 

```

---

### Post by grahammechanical on 2015-05-06
If I am understanding you correctly you can with a little trickery load Ubuntu. Have you tried loading Ubuntu and then running

```
sudo update-grub
```

Grub looks for configuration files in /boot/grub/ I am wondering if the grub that you have installed knows where to find its configuration files.

Regards.

---

### Post by miatawnt2b on 2015-05-07
I have tried update-grub and I get the same thing. Drops right into grub command line.

---

### Post by miatawnt2b on 2015-05-08
bump

---

### Post by miatawnt2b on 2015-05-11
still working on it with no luck. any ideas?

---

