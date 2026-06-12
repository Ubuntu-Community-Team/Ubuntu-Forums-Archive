---
title: "Grub Error 15 for new Kernels"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by pear on 2007-05-11
I upgraded from Edgy to Feisty expecting to get rid of a problem with new kernels. But I still have the problem. I can use my 2.6.17-10 kernel but if I try to run any other kernel it comes up grub error 15.
Currently I have 2.6.20-15-generic installed but not working and I've tried completely reinstalling it.

Here is my grub config from /boot/grub/menu.lst:

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a88bdcf3-7afe-441f-82b3-823dc17b5138 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a88bdcf3-7afe-441f-82b3-823dc17b5138 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a88bdcf3-7afe-441f-82b3-823dc17b5138 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=a88bdcf3-7afe-441f-82b3-823dc17b5138 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin


These are the files in my boot directory all with the same permissions
abi-2.6.17-10-generic             initrd.img-2.6.17-11-generic.bak
abi-2.6.20-15-generic             initrd.img-2.6.20-15-generic
config-2.6.17-10-generic          memtest86+.bin
config-2.6.20-15-generic          System.map-2.6.17-10-generic
grub                              System.map-2.6.20-15-generic
initrd.img-2.6.17-10-generic      vmlinuz-2.6.17-10-generic
initrd.img-2.6.17-10-generic.bak  vmlinuz-2.6.20-15-generic


All seems well as the files referred to are in the boot directory and everything seems the same between the two kernels. I've loaded a live CD and tried reinstalling the grub but it made no difference.

I did notice errors with mdadm during the update so I guess that might have something to do with it. I also installed the previous version of Kubuntu to my other physical hard drive but I removed the bootable flag from it after these problems started.

Any ideas ? Thanks.

---

