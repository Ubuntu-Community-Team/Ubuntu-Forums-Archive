---
title: "Safely and easily removing old Linux and initrd images."
date: 2019-04-11
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-04-11
Whenever I update the kernel and generate a new grub configuration file I get a list of old images like the list below. Often that kernel version has long been removed How can I safely and easily remove these?

```

Found linux image: /boot/vmlinuz-4.4.0-145-generic
Found initrd image: /boot/initrd.img-4.4.0-145-generic
Found linux image: /boot/vmlinuz-4.4.0-142-generic
Found initrd image: /boot/initrd.img-4.4.0-142-generic
Found linux image: /boot/vmlinuz-4.4.0-138-generic
Found initrd image: /boot/initrd.img-4.4.0-138-generic
Found linux image: /boot/vmlinuz-4.4.0-112-generic
Found initrd image: /boot/initrd.img-4.4.0-112-generic
Found linux image: /boot/vmlinuz-4.4.0-103-generic
Found initrd image: /boot/initrd.img-4.4.0-103-generic
Found linux image: /boot/vmlinuz-2.6.32-31-generic
Found initrd image: /boot/initrd.img-2.6.32-31-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
```

---

### Post by TheFu on 2019-04-11
```
sudo apt autoremove
``` works on 16.04 and later.
If it doesn't, post back and there are scripts.

Removing the left over kernels from prior releases is manual, methinks.  Just get the package name and remove it.
```
dpkg -l |grep linux-image-2.
``` will find the 2.6 kernel package name.

---

### Post by rsteinmetz70112 on 2019-04-11
```
# apt autoremove
``` 
Doesn't work for these old files. It does work when a new kernel is installed.

---

### Post by TheFu on 2019-04-11
Try, **sudo apt-get autoremove linux-image-4.4.0-1[0-3]* linux-image-2.***
apt-get works with regex.

---

### Post by TheFu on 2019-04-11
Try, **sudo apt-get remove linux-image-4.4.0-1[0-3]* linux-image-2.***
apt-get works with regex.

Update:    autoremove --> remove above.

---

