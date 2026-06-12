---
title: "Error on executing &quot;sudo dpkg --configure -a&quot; Cannot find /lib/modules/2.6.24-19-386"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Sudeep Ambekar on 2008-08-21
Hi,

I am getting following error on executing "sudo dpkg --configure -a"

Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-386
Cannot find /lib/modules/2.6.24-19-386
update-initramfs: failed for /boot/initrd.img-2.6.24-19-386
dpkg: subprocess post-installation script returned error exit status 1

When I checked my lib folder it had following folder
/lib/modules/2.6.24-19-generic
this problem started After I tried installing bittorent client bittorrent_5.2.0_python2.4.deb

---

