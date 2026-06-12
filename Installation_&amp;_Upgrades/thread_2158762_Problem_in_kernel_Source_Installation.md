---
title: "Problem in kernel Source Installation"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by subhajit123 on 2013-06-30
I want to install kernel source in Ubuntu 12.04 which is not installed. I have checked the same using the following command :


dpkg -s kernel


Output is Kernel is not installed no information available


Hence I have followed the following steps to install the same:


1.Installed the Dependencies by the following command:


$ sudo apt-get install gcc libncurses5-dev git-core kernel-package fakeroot build-essential
$ sudo apt-get update && sudo apt-get upgrade


2. Download kernel source by the following command:
$ wget [http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.5.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.5.tar.bz2)
$ tar -xvf linux-3.5.tar.bz2
$ cd linux-3.5/


3.Compiled the source code to generate the .deb packages by the following command


$ make-kpkg clean
$ fakeroot make-kpkg --initrd --append-to-version=-spica kernel_image kernel_headers


4. Install the .deb packages (two .deb packages generated, one is to install the kernel headers, another one is to install the kernel image) by the following command


$ sudo dpkg -i linux-*.deb


But after reboot it seems kernel is not installed (checked by dpkg -s kernel). Pls tell where I am wrong.
Also, In step 3, I guess i am installing a new kernel (named spica kernel_image) but during the boot up this new kernel is not showing as option. Pls help me

---

### Post by Cheesemill on 2013-06-30
Try updating grub...
```
sudo update-grub
```

You can also look in the /boot directory to see if your new kernel has been installed properly.

---

