---
title: "Problem installing a new kernel from source"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by booki on 2012-09-30
Just for practice I tried for my very first time to install a new kernel from source. 
I tried it in a virtual machine (Virtual Box) running Ubuntu 12.04. I didn’t want to download and install  the debian files. I used the following known commands:
mkdir  /home/alexandros/linux_test
cd linux_test
wget [http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.5.4.tar.bz2](http://www.kernel.org/pub/linux/kernel/v3.0/linux-3.5.4.tar.bz2)
tar –xjvf linux-3.5.4.tar.bz2
cd linux-3.5.4
make defconfig       (it is my first time!!!!)
make
sudo make modules_install
sudo make install
sudo update-initramfs -c -k all

After the installation I can the see the new kernel in the grub menu but I take the following message. 
[ATTACH]224898[/ATTACH]

Can anyone help me?

---

### Post by Doug S on 2012-09-30
Hi and welcome to Ubuntu forums.
 
I am not certain, but your issue might be because you are using the default configuration for the kernel compile. Look at the config files in your /boot directory. Example:```
-rw-r--r-- 1 root root   140454 Jul  6 08:06 config-3.2.0-27-generic
-rw-r--r-- 1 root root   140432 Jul 27 10:44 config-3.2.0-29-generic
-rw-r--r-- 1 root root   140432 Aug 24 10:33 config-3.2.0-30-generic
-rw-r--r-- 1 root root   140459 Sep  7 09:57 config-3.2.0-31-generic
``` and decide on one as your starting point config file for your compile, and then at least you are starting with something that should work for your system.```
cp /boot/config-3.2.0-31-generic .config
```Note: My own notes on compiling a kernel from kernel.org are a little vaque, so I might not have it correct, but I hope it helps.

---

