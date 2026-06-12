---
title: "update-initramfs errors out on dist-upgrade"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by bmvbab on 2011-05-31
Im upgrading from 10.04 to 11.04, I have used apt-get dist-upgrade to do the upgrade. All packages have been updated except the kernel. There are issues while upgrading the kernel. Any pointers please...

#apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.98.8ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Warning: No support for locale: en_IN
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-8-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-8-generic; however:
  Package linux-image-2.6.38-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.38.8.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):No apport report written because the error message indicates its a followup error from a previous failure.

 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.38.8.22); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
            Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Warning: No support for locale: en_IN
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.35-28-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-8-generic
 linux-image-generic
 linux-image
 linux
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by bmvbab on 2011-05-31
[http://ubuntuforums.org/showthread.php?p=10723612](http://ubuntuforums.org/showthread.php?p=10723612)
[http://blog.jorgeivanmeza.com/2011/05/actualizar-gnulinux-mint-10-julia-a-11-katya-mediante-apt/](http://blog.jorgeivanmeza.com/2011/05/actualizar-gnulinux-mint-10-julia-a-11-katya-mediante-apt/)

The above solved my problem.

---

