---
title: "Error Help"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by Irfan_Mulla on 2015-05-08
Hi

I have ubuntu 12.04 installed and get the following error message when trying to do the update

Setting up initramfs-tools (0.99ubuntu13.5) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-39-generic
cp: reading `/sbin/udevadm': Input/output error
cp: failed to extend `/tmp/mkinitramfs_nAaeCn//sbin/udevadm': Input/output error
E: /usr/share/initramfs-tools/hooks/udev failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.8.0-39-generic with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot see my desktop as well wont come up. PC does boot up could someone advise how I can solve. Thanks

---

### Post by bapoumba on 2015-05-09
Input/output error may mean the file system has errors or some partitions are full (most probably the first one..).
Please post the output to :
```
df -h
df -i
```

---

