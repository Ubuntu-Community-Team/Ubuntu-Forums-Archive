---
title: "Upgrade problems"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by rickry on 2018-02-02
Hi,

I have a error when i upgrade ubuntu server 16.04
This is my output:

root@Server:/var/www# apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-101 linux-headers-4.4.0-101-generic linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic linux-image-4.4.0-101-generic linux-image-4.4.0-97-generic
  linux-image-extra-4.4.0-101-generic linux-image-extra-4.4.0-97-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-firmware (1.157.15) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-104-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-104-generic with 1.
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-112-generic (4.4.0-112.135) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-109-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-112-generic /boot/vmlinuz-4.4.0-112-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-112-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-112-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-112-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-112-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-112-generic:
 linux-image-extra-4.4.0-112-generic depends on linux-image-4.4.0-112-generic; however:
  Package linux-image-4.4.0-112-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-112-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-112-generic; however:
  Package linux-image-4.4.0-112-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-112-generic; however:
  Package linux-image-extra-4.4.0-112-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.112.118); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-109-generic (4.4.0-109.132) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-112-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-109-generic /boot/vmlinuz-4.4.0-109-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-109-generic /boot/vmlinuz-4.4.0-109-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-109-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-109-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-109-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-109-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-109-generic:
 linux-image-extra-4.4.0-109-generic depends on linux-image-4.4.0-109-generic; however:
  Package linux-image-4.4.0-109-generic is not configured yet.


dpkg: error processing package linux-image-extra-4.4.0-109-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-firmware
 linux-image-4.4.0-112-generic
 linux-image-extra-4.4.0-112-generic
 linux-image-generic
 linux-generic
 linux-image-4.4.0-109-generic
 linux-image-extra-4.4.0-109-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Impavidus on 2018-02-02
Sounds like a full /boot partition.

Which kernel do you run now?```
uname -r
```If at least 4.4.0-104, uninstall some old kernels:```
sudo dpkg --purge linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic linux-image-4.4.0-97-generic linux-image-extra-4.4.0-97-generic
sudo dpkg --purge linux-headers-4.4.0-101 linux-headers-4.4.0-101-generic  linux-image-4.4.0-101-generic linux-image-extra-4.4.0-101-generic
```Then try and fix it with```
sudo apt install -f
```
Better use autoremove before it fills up.

---

### Post by rickry on 2018-02-02
Thank you very much it works!

---

