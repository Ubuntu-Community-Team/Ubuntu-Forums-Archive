---
title: "upgardation of kernel version of Ubuntu 11.10 from 3.0.0.2 to 3.1.6"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by uygr on 2012-02-02
hey i face the following problem while updating the kernel of Ubuntu 11.10
can any on suggest me the solution

I used following steps:
tar -xzvf source directory
make defconfig
make menuconfig
make modules
make bzImage
make modules_install
make install
reboot

---

### Post by xyzzyman on 2012-02-02
That's probably not the best way to be doing it on a debian based OS. Take a look at [http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/](http://blog.avirtualhome.com/2012/01/13/compile-linux-kernel-3-2-for-ubuntu-11-10/) and [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

Also you should know that by using the 3.1 mainline kernel sources, you're not getting all the patches and optimizations that Ubuntu performs. For one ureadahead and apparmor break as the necessary patches will be gone.

As far as you not booting, you may have disabled things while doing the makemenuconfig, or you may have not enabled something that you need to access the drive that you mounted your /root directory on... Did you actually put /root on a different partition than / though??

---

