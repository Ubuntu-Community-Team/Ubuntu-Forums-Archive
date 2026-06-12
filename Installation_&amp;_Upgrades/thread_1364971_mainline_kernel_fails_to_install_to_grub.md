---
title: "mainline kernel fails to install to grub"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2009-12-26
as part of trying to sort out a bug, ive been directed to mainline kernel installation, following this

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

ros@ros-laptop:/boot/grub$ cd /home/ros/Desktop/
ros@ros-laptop:~/Desktop$ ls
linux-headers-2.6.31-02063104_2.6.31-02063104_all.deb
linux-headers-2.6.31-02063104-generic_2.6.31-02063104_i386.deb
linux-source-2.6.31_2.6.31-02063104_all.deb

ros@ros-laptop:~/Desktop$ sudo dpkg -i *.deb
(Reading database ... 170946 files and directories currently installed.)
Preparing to replace linux-headers-2.6.31-02063104 2.6.31-02063104 (using linux-headers-2.6.31-02063104_2.6.31-02063104_all.deb) ...
Unpacking replacement linux-headers-2.6.31-02063104 ...
Preparing to replace linux-headers-2.6.31-02063104-generic 2.6.31-02063104 (using linux-headers-2.6.31-02063104-generic_2.6.31-02063104_i386.deb) ...
Unpacking replacement linux-headers-2.6.31-02063104-generic ...
Preparing to replace linux-source-2.6.31 2.6.31-02063104 (using linux-source-2.6.31_2.6.31-02063104_all.deb) ...
Unpacking replacement linux-source-2.6.31 ...
Setting up linux-headers-2.6.31-02063104 (2.6.31-02063104) ...
Setting up linux-headers-2.6.31-02063104-generic (2.6.31-02063104) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-source-2.6.31 (2.6.31-02063104) ...


and it doesnt appear in menu.1st

ros@ros-laptop:~/Desktop$ grep ^[a-z] /boot/grub/menu.lst
default		0
timeout		3
hiddenmenu
title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet
title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic
title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet
title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic
title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet
title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
title		Ubuntu 9.10, kernel 2.6.27-11-generic
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet
title		Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=95ae6c41-2e06-45a1-a55c-fab8300a4836 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic
title		Ubuntu 9.10, memtest86+
uuid		95ae6c41-2e06-45a1-a55c-fab8300a4836
kernel		/boot/memtest86+.bin
quiet
ros@ros-laptop:~/Desktop$

---

### Post by darco on 2009-12-26
looks like you are missing the kernel image:

linux-image-2.6.31-020631-generic_2.6.31-020631_i386.deb

I never d/l the source as you did.
Also if you have grub2, dont forget to run sudo update-grub but it does normally run that command automatically when the kernel is updated.

darco

---

### Post by pdc124 on 2009-12-26
so are the instructions here [https://wiki.ubuntu.com/KernelTaeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTaeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

(half way down the page),  incomplete ?

---

### Post by darco on 2009-12-26
Not sure about the 2nd link you posted, but to me it seems that you d/l the wrong file. 

darco

---

### Post by sgosnell on 2009-12-26
To install the mainline kernels, just download the appropriate linux-image file for your hardware, then use gdebi to install it.  Quick and easy, no need for anything else if you're just going to use it on a standard desktop system.  If you're going to be developing apps, then you need the headers, but most people don't do that.

---

