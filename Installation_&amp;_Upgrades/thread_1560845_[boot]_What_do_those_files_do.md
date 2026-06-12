---
title: "[boot] What do those files do?"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by littlebigman on 2010-08-25
Hello

While running "apt-file show linux-image-2.6.31-22-generic", I notice those files in /boot:

```

linux-image-2.6.31-22-generic: /boot/System.map-2.6.31-22-generic
linux-image-2.6.31-22-generic: /boot/abi-2.6.31-22-generic
linux-image-2.6.31-22-generic: /boot/config-2.6.31-22-generic
linux-image-2.6.31-22-generic: /boot/vmcoreinfo-2.6.31-22-generic
linux-image-2.6.31-22-generic: /boot/vmlinuz-2.6.31-22-generic

```

Does someone know what those files do exactly? Why is there no initrd.(gz/lz), since I read that to keep the kernel (vmlinuz) small, most drivers are not part of it and must be loaded dynamically (from initrd while the kernel is still booting up, and from the real root filesystem once the mass-storage can be mounted)?

Thank you.

---

