---
title: "grub2 setup errors on external drive; can boot manually"
date: 2016-03-16
forum: Installation &amp; Upgrades
---

### Post by qyot27 on 2016-03-16
Lubuntu (I actually installed 16.04 Beta1 rather than 15.10 like I usually would, just to get at kernel 4.4) did install correctly to this drive during the install process, but because grub2 and UEFI and external USB hard drives are such a rat's nest, I can't get it to set up grub2 correctly.

I've managed to get as far as the boot entry taking me to the grub2 command line, and from there, I can point it at the correct linux kernel and initrd images and manually boot.  From that point on, everything's fine.  But I'm at a loss for how to actually get grub installed correctly so I don't have to keep doing that every time.

Some stats:
The PC itself is a Quantum Byte (32-bit Windows 10, Atom Z3735F, 2GB RAM), which means 32-bit UEFI.  Lubuntu is 64-bit because the Z3735F is a Silvermont and mixed-mode UEFI has been supported by both the kernel and by Ubuntu (and kin) for a while now.

The output of *sudo update-grub2*:
```
$ sudo update-grub2
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-13-generic
Found initrd image: /boot/initrd.img-4.4.0-13-generic
Found linux image: /boot/vmlinuz-4.4.0-7-generic
Found initrd image: /boot/initrd.img-4.4.0-7-generic
blockdev: ioctl error on BLKROSET: Operation not permitted
Found Windows Boot Manager on /dev/mmcblk0p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
```
The part that I'm sure is the problem is the *blockdev: ioctl error on BLKROSET: Operation not permitted* line.

My main reason for installing to an external hard drive is that the eMMC storage in this PC is only 32GB, and Windows (along with the other programs I use and the massive size of VS Community 2015) takes up all but ~6GB of it.  So having Lubuntu on the external drive is nicer: the partition breakdown on the external is:
```
1GB FAT32 EFI System Partition
20GB ext4 /
2GB swap
25GB ext4 /home
30GB NTFS shared storage
```

---

### Post by xjesus on 2016-04-09
Same problem here with XJubunTAB installation on a external USB drive and /boot/efi located on internal eMMC. My device is Teclast X98 Plus.

I attach capture here [http://i.imgur.com/8LHc7UM.png](http://i.imgur.com/8LHc7UM.png)[http://i.imgur.com/8LHc7UM.png]("http://i.imgur.com/8LHc7UM.png")

---

### Post by xjesus on 2016-04-09
Anyhow it has worked following this guide
[http://forum.xda-developers.com/x98-air/general/guide-install-ubuntu-teclast-tablets-t3352310](http://forum.xda-developers.com/x98-air/general/guide-install-ubuntu-teclast-tablets-t3352310)
and in my case I had to boot with
linux (hd1,msdos5)/vmlinuz root=/dev/sdb5
initrd (hd1,msdos5)/initrd.img
boot

then later I did "sudo grub-install" and "sudo update-grub"

---

### Post by celsus on 2016-07-06
I'm having the same error trying to install Xubuntu 16.04 to a 32GB Sandisk Ultra Fit on my Kangaroo (Atom X5-Z8500), but I cannot boot manually.  Following the procedure described does no good; GRUB declares that there is no /dev/sda2, although that is what is in /etc/fstab and the USB 3 slot is assigned /sda -- that is the right partition alright.  Some of the errors scrolling by are attributed to overcurrent demands by Paul Phillipov, but his solution is to replug devices and power cycle the device, which has done nothing to resolve them.  Windows 10 boots from the internal aMMC just fine and the Sandisk seems OK for other purposes too.  No idea how to proceed.

---

