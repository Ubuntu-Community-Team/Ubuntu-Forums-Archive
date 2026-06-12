---
title: "what is the best way to compile a kernel?"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by erogol on 2011-02-19
I tried to compile the Kernel 2.6.37.1 and use it but I have not done that properly. I guess there are two ways to do that:
1. Use "make" commands and mkinitrd command to create initrd file.
2. use such commands:
p -vi /boot/config-`uname -r` .config

make localmodconfig

fakeroot make-kpkg --initrd --append-to-version=okan kernel-image kernel-headers

sudo dpkg -i linux-ubuntu-modules-2.6.24-16-generic_2.6.24-16.23_i386.deb
sudo dpkg -i linux-headers-lum-2.6.24-16-generic_2.6.24-16.23_i386.deb

cd /boot
sudo update-initramfs -c -k 2.6.37+QD

sudo update-grub2
reboot

which one is the prober one or is there any way to do that?

---

### Post by dino99 on 2011-02-19
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

[http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html](http://linuxtweaking.blogspot.com/2010/05/how-to-compile-kernel-on-ubuntu-1004.html)

[http://www.question-defense.com/2010/09/26/how-to-recompile-your-ubuntu-10-10-kernel-for-patching-or-to-add-support-for-a-specific-device](http://www.question-defense.com/2010/09/26/how-to-recompile-your-ubuntu-10-10-kernel-for-patching-or-to-add-support-for-a-specific-device)

and the ready to use:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

