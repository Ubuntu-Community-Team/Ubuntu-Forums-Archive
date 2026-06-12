---
title: "How to install Ub6.10 from hard drive"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by EastIN on 2007-02-19
PC doesn`t have DVD. I copy distib on /boot/install, configured grub like this:

title Ubuntu
root (hd1,1)
kernel   /boot/install/casper/vmlinuz preseed/file=/boot/install/preseed/ubuntu.seed boot=casper ramdisk_size=1048576 root=/dev/ram
initrd /boot/install/casper/initrd.gz

Load fails errors like : cannot mount /proc on /root/proc

I read all docs about it and stuck. Please help :confused:

---

### Post by tgalati4 on 2007-02-22
How much RAM does your system have?  Your ramdisk needs to be smaller than the actual RAM to allow for housekeeping.  /proc is where all this housekeeping is kept.  If there is no room for it, then you might get this strange error.

---

