---
title: "Can't install package"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by laloruelas on 2011-04-30
whenever i try to install or uninstall a package dpkg gives me an error. i dont know how to fix it. here is my output> 
eduardo@lalo-laptop:~$ sudo apt-get install grub-customizer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  hwinfo libhd16
The following packages will be REMOVED:
  linux-image-2.6.32-23-generic
The following NEW packages will be installed:
  grub-customizer hwinfo libhd16
0 upgraded, 3 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 1,023 kB of archives.
After this operation, 95.8 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/) natty/main grub-customizer i386 2.1.2-0ubuntu1~ppa1n [279 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe libhd16 i386 16.0-2 [698 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/universe hwinfo i386 16.0-2 [46.1 kB]
Fetched 1,023 kB in 14s (69.7 kB/s)                                            
(Reading database ... 229112 files and directories currently installed.)
Removing linux-image-2.6.32-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
Generating grub.cfg ...
Found background image: Aurora.png
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
tail: cannot open `(copy)' for reading: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.32-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)fixed by itself

---

