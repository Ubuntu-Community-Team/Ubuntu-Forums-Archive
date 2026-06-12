---
title: "Problem to install kernel in ubuntu 7.04"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by nadavvin on 2007-01-14
```

Setting up linux-image-2.6.20-5-generic (2.6.20-5.7) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-5-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.20-5.7 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.20-5.7 was configured last, according to dpkg)
The provided postinst hook script [/sbin/update-grub] could not be run.
dpkg: error processing linux-image-2.6.20-5-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-5-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What to do?

---

### Post by nadavvin on 2007-01-20
No one is using in ubuntu 7.04???

---

### Post by rlozano on 2007-01-24
i believe there are still very few using herd, as this is only RC2 and we don't expect any stability from this release... :-)

---

### Post by Caligula on 2007-02-16
aptitude install grub

---

