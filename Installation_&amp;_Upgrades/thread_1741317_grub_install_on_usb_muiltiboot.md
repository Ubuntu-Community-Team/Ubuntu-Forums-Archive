---
title: "grub install on usb muiltiboot"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by gpost3 on 2011-04-28
hi,
I have ubuntu 10.10 running and I want to make a multiboot usb flash drive. I have iso images of ubuntu live cd, windows, acronis and memtest86 which I intend to put in the usb. My fdisk -l shows:

```
root@ubuntu:/home/abid# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x473eb788

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60802   488384001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x674f31a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13053   104845534+   7  HPFS/NTFS
/dev/sdb2           13053       55263   339050273+   7  HPFS/NTFS
/dev/sdb3           55263       60802    44489728   83  Linux

Disk /dev/sdc: 4000 MB, 4000317440 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008c7f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1016     3905473   83  Linux

```I think sdc is my usb drive.
On terminal, I did:

```
sudo grub-install /dev/sdc
```which returned following:

```
Searching for GRUB installation directory ... found: /boot/grub
``` and got stuck there. Where am I going wrong?

---

### Post by gpost3 on 2011-04-28
Did some research, it may be a better idea for me to use Grub2. Anyone please help?

---

### Post by wilee-nilee on 2011-04-28
You can do it easier with the several multiboot programs out there. Here is one that I use there is a windows version called yumi as well on this same site.
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

There is a command line one as well I can't find it right now and there are sites that will tell you how to load grub2 to a thumb and use it. You can't just load the mbr there has to be the rest of the grub setup in the partition.

I think it is fairly straight forward to install grub and use it the way you ask, but personally since the multiload tools work so I well, I don't bother with a manual setup.

---

### Post by gpost3 on 2011-04-28
thank you so much for your reply. I like the link you gave (will try it out) but I also managed to install grub2 on my usb was fairly easy as you pointed out. Now I am trying to modify the grub.cfg. By the way, I am running Ubuntu 10.10 as my main (and only) operating system right now.

This is what my menu entries look like, I have also taken care of UUID using blkid in ubuntu. All I need to know is how do I create the menu entries for .bin and .iso image files in grub.cfg?

Here is a portion of mine right now:
```
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 63d6aab9-f9ff-49ce-8290-809e697b39ef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos3)'
    search --no-floppy --fs-uuid --set 63d6aab9-f9ff-49ce-8290-809e697b39ef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
```As you can see, it is pointing to a MemTest program which already came with my ubuntu install. I want to point it to look for memtest .bin file inside the usb drive.

~cheers as I made some decent progress!

---

### Post by wilee-nilee on 2011-04-28
Here you go this should get you set look at post #6.
[http://ubuntuforums.org/showthread.php?p=10088785](http://ubuntuforums.org/showthread.php?p=10088785)

A lot of info there but the poster is quite good at this.

---

### Post by gpost3 on 2011-04-28
That is a lot of info there. I tired the pendrive tool, upon clicking validate, it just quits. Anyway I want to add the memtest entry and also ubuntu entry to my grub2 as I am quite close. I have downloaded Ubuntu Live CD (iso image) and the memtest.bin. How do I shape my menuentry in grub.cfg?

---

### Post by wilee-nilee on 2011-04-28
> **gpost3 said:**
> That is a lot of info there. I tired the pendrive tool, upon clicking validate, it just quits. Anyway I want to add the memtest entry and also ubuntu entry to my grub2 as I am quite close. I have downloaded Ubuntu Live CD (iso image) and the memtest.bin. How do I shape my menuentry in grub.cfg?

The only oddity I have found with the pendrive tool the linux use one is that the thumb needs to be formatted with gparted, which you can install in your Ubuntu install. Otherwise I get a fail to load or reload the grub to the mbr when it starts up.

I had not been sure about this part as I use gparted all the time anyway to format and such.

---

### Post by C.S.Cameron on 2011-04-28
Try MultiBootUSB, it is a script that is real easy to use.
You can put dozens of distros on a single drive, (if you have room).
You must be booted from a distro that uses grub2 to use it, (such as the Live CD).

---

