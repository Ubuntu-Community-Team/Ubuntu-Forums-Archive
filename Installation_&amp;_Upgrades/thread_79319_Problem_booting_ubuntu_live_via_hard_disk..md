---
title: "Problem booting ubuntu live via hard disk."
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by balajint on 2005-10-20
Hello all,

I use a computer without a CD drive. I always try the live cds by using a fat32 partition. I copy the compressed image and kernel to the fat32 partition and put in appropriate GRUB entries to boot the live distro. 

I have tried a number of such distros and have been succesful with the previous versions of Ubuntu. Since the change in live cd boot process from 5.04; Ive been using a seperate kernel image from Ubuntu and the live cd iso to execute the task.

In similar fashion I used the hd-image kernel from 

[http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/hd-media/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/hd-media/boot.img.gz)

and used the following GRUB entry


title Breezy-Badger-Hd-image
kernel (hd0,2)/breezy/linux vga=791 ramdisk_size=12776 root=/dev/rd/0 rw  --
initrd (hd0,2)/breezy/initrd.gz

I also had the following cd iso in my fat32 partition

ubuntu-5.10-live-i386.iso

Normal procedure is ; when the hd-image kernel boots; it searches for an installer iso and it finds the live cd iso and transfers the control to it. 

In the case of 5.10 ; the hd-image installer is able to recongnize the live cd iso but fails at timezone selection.

Can anyone help me out with this problem. I am not able to bypass timezone selection from the Ubuntu installer. Is this a bug with the installer kernel or what ?

If you are not able to understand the problem; then I am only too eager to explain it in detail.

Thanks

Balaji

---

