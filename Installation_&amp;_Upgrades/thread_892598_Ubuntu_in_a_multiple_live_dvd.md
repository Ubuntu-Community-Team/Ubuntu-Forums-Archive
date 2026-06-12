---
title: "Ubuntu in a multiple live dvd"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Israeru on 2008-08-17
Hello

I am tryng to make a custom live dvd with multiple live cds, but Ubuntu Hardy don´t boot. (Sorry for my bad english)

Ubuntu don´t find the image of the filesystem, see the screenshots:

[http://img46.imageshack.us/img46/8868/errorubuntuog1.png](http://img46.imageshack.us/img46/8868/errorubuntuog1.png)

This is the isolinux config that i use:


default Mandriva One KDE
prompt 1
timeout 40
gfxboot /boot/syslinux/bootlogo
label Mandriva One KDE
kernel /boot/vmlinuz
append initrd=/boot/cdrom/initrd.gz splash=silent vga=788

label SUSE 11 KDE 4.1
kernel /boot/suse/linux
append initrd=/boot/suse/initrd ramdisk_size=512000 ramdisk_blocksize=4096 splash=silent

label Fedora 9
kernel /boot/grub/fedora/vmlinuz0
append initrd=/boot/grub/fedora/initrd0.img rhgb root=CDLABEL=SFD rootfstype=iso9660 ro quiet liveimg

label Knoppix 5.1
kernel /boot/grub/knoppix/linux
append initrd=/boot/grub/knoppix/minirt.gz ramdisk_size=100000 init=/etc/init lang=es apm=power-off vga=791 nomce splash BOOT_IMAGE=knoppix

label Ubuntu Hardy
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/preseed/ubuntu.seed boot=casper bootkbd=es quiet 

Help please n_n

---

