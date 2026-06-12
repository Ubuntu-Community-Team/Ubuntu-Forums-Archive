---
title: "Upgrade from 8.04 to 8.10 - cant boot 2.6.27-7 kernel"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by akrapacs on 2008-11-12
I've just upgraded my machine from 8.04 to 8.10. Immediately after the upgrade the machine refused to boot the default version of the kernel, which is 2.6.27-7-generic. It does boot the previous versions just fine, which is 2.6.24-21-generic. 

When I try to boot 2.6.27-7-generic in normal mode, I get the following error:

"Gave up waiting for root device...
...
ALERT! /dev/disk/by-uuid/... does not exist. Dropping to a shell!"

Screenshot: [http://idisk.me.com/akrapacs-Public/ubuntu_boot.jpg](http://idisk.me.com/akrapacs-Public/ubuntu_boot.jpg)

When I try to boot 2.6.27-7-generic in recovery mode, the boot hangs.

Screenshot: [http://idisk.me.com/akrapacs-Public/ubuntu_boot_recovery.JPG](http://idisk.me.com/akrapacs-Public/ubuntu_boot_recovery.JPG)

Below is a snippet of my menu.lst file. As you can see the exact same UUID is specified for both of the kernels, and yet I still can not boot the newest one. I have also tried changing the uuid in the kernel command to /dev/sda1 or (hd0,0) and neither solved the problem. Is it possible that this version of the kernel is corrupt on my system?

```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0a03c220-7935-45eb-88fc-d0cbab3aa94b ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by akrapacs on 2008-11-12
After continuing to find a resolution I've actually solved my problem. I followed the suggestions in the first screenshot and added "rootdelay=60" after "root=..." and now both normal and recovery mode boot fine for all kernels. The reason I didn't try this before is because the version of the kernel that was booting fine will boot fine without this parameter.

---

### Post by jimbudler on 2008-11-12
This is apparently an issue with SATA drives.

Because of the same concern I added it using the kopt_X_Y_Z so it only effects the 2.6.27 kernel

# kopt=root=UUID=6a0b60d6-1744-4fb0-8b1b-05b37f215e01 ro
# kopt_2_6_27=root=UUID=6a0b60d6-1744-4fb0-8b1b-05b37f215e01 ro rootdelay=60

Jim

---

### Post by ubiubi on 2008-11-14
This is apparently an issue with SATA drives.

Because of the same concern I added it using the kopt_X_Y_Z so it only effects the 2.6.27 kernel

# kopt=root=UUID=6a0b60d6-1744-4fb0-8b1b-05b37f215e01 ro
# kopt_2_6_27=root=UUID=6a0b60d6-1744-4fb0-8b1b-05b37f215e01 ro rootdelay=60

Jim

Hi Jim

I have a similar problem after upgrading from Hardy. It only allows me to bootup from the older kernal.

I'm not very experienced and I don't exactly follow your description of the problem resolution.

What is KOPT_X_Y_Z  ?

What file do I have to alter? And where do I find it. Would I have to use the sudo nautilus command to get the root permission?

Thanks for your patience!

---

