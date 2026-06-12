---
title: "Installing to external USB HD without grub"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by esullivan on 2010-06-08
I am trying to install 10.04 to an external HD (not flash).  I ran the live CD, installed to it and all seemed to work fine, but I don't want to use GRUB.  I ran 7 repair and did a bootrec /fixmbr and it's booting normal, but I can't boot to USB.

I want it to boot normal, unless I hit F12 to boot to removable device.

Can this be done.  Not much of a Linux person, but I am trying to be.

Thanks!
Evan

---

### Post by pytheas22 on 2010-06-08
I may be wrong, but I'm pretty sure you need to install GRUB (or some other bootloader capable of booting Linux) somewhere on your computer in order to be able to boot your Ubuntu installation.  It doesn't have to be on your main hard drive, but it has to be somewhere.  I don't think Windows' boot loader can boot a Linux kernel.

When you install Ubuntu, you should be able to tell it to install GRUB to the USB stick, rather than to your internal hard disk (if I recall correctly, you have to select "Advanced" in the last or second-to-last screen of the Ubuntu installer in order to specify where GRUB should be installed).  That way, it won't mess with Windows' MBR or any of that.  Then when you want to boot to Ubuntu, you would hit F12 and select the USB device; otherwise, your BIOS would boot to your internal hard disk (which I presume has Windows on it) as normal.

---

### Post by darkod on 2010-06-08
Yes, windows bootloader can't boot linux. And for what you want to achieve, you only needed to tell grub2 to install on the usb hdd.

But you don't need to reinstall ubuntu for that. Boot again in live mode with the usb hdd connected, post the result of:

sudo fdisk -l (small L)

and we'll give you the commands to add grub2 to the ext hdd.

---

### Post by esullivan on 2010-06-08
Thanks guys, here you go:

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6a00352f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       15566   124930048    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb74cc1e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9328    74920960   83  Linux
/dev/sdc2            9328        9730     3227649    5  Extended
/dev/sdc5            9328        9730     3227648   82  Linux swap / Solaris
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

USB drive is SDB1

---

### Post by darkod on 2010-06-08
Hold on, I thought you said you installed ubuntu on the usb hdd. Ubuntu is on /dev/sdc.

And you say the usb hdd is /dev/sdb.

Are we missing something?

---

### Post by esullivan on 2010-06-08
Its the 80GB HD.  Yes its an external HD (not usb flash)

My fault I read it wrong.

---

### Post by darkod on 2010-06-08
OK, from live mode in terminal execute:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

Job done. Your computer should boot windows directly, but if you select the usb hdd in the quick boot menu you should see grub2.

---

### Post by esullivan on 2010-06-08
Thank you!

---

