---
title: "Upgraded to new kernel...lots of hard disk space used up.."
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by scottptn on 2008-06-20
Hi,

I am using Ubuntu 8.04 . My kernel release version is 2.6.24-generic . I recently downloaded the latest kernel source (v2.6.25.7) from kernel.org. 
I compiled the kernel and installed it in the following way :

```


Step 1) tar -jxvf linux-2.6.25.7.tar.bz2

Step 2)ln -s /usr/src/linux-2.6.25.7/ /usr/src/linux

Step 3)I copied my old config file (config2.6.24-16-generic) from /boot  to  /usr/src/linux

Step 4) make gconfig (Kept all settings unchanged except I just set processor family, disabled ISA and MCA and turned on Advanced Linux Sound Architecture )

Step 5) make

Step 6) make modules_install

Step 7) make install

Step 8) cd /boot/

Step 9) mkinitramfs -o initrd.img-2.6.25.7 2.6.25.7

Step 10) update grub


```

This is the first time i compiled and installed a kernel myself, so i dont know whether i did it right.
So, now i want to uninstall the new kernel and undo any changes i made while installing it for the following two reasons

1) When i try to boot the new kernel it causes a Kernel Panic.

2) A lot of my hard disk space is being used up after this install (probably because some new programs got installed that i dont know of) and i dont know what to uninstall to get that space back.

Any help in this regards would be really appreciated.

Thank You.

---

### Post by Iandefor on 2008-06-20
1) When you copied your old kernel config over, did you rename it to .config?
2) Did you run ```
make oldconfig
```Before modifying your configuration? You need to do that to make sure that the old configuration is applied first.

Regarding the disk space being used up, do you have a sense of how much more is being taken up, and can you pinpoint where it's all being used using the disk usage analyzer tool (Applications->Accessories->Disk Usage Analyzer)? If it's in the kernel source directory, running make clean might help.

---

