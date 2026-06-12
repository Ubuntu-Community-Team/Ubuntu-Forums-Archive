---
title: "Install kernel 4.10.0-37 in Ubuntu 17.10"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2017-10-26
I give up no amount of fixes work for me with the kernel, gdm3 and Nvidia.  If possible can I install kernel 4.10.0-37. and how to do it.

Henry

---

### Post by Kirboosy on 2017-10-27
Without a bunch of manual labor I think your best bet might to be install 16.04. From there you can install install the kernel with apt or apt-get.

```
sudo apt install linux-image-4.10.0-37-generic linux-headers-4.10.0.37
```

From there grub should be updated to use the kernel and you should be good to go.

---

