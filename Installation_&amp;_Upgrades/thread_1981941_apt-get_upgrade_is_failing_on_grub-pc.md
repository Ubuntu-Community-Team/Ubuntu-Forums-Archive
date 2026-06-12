---
title: "apt-get upgrade is failing on grub-pc"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Skerit on 2012-05-17
I've installed ubuntu 12.04 just fine, but my latest apt-get upgrade ran into some problems.

Basically: it hangs on creating a grub config file.

```

sudo dpkg --configure -a
Instellen van grub-pc (1.99-21ubuntu3.1) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-20-generic
Found initrd image: /boot/initrd.img-3.2.0-20-generic
Found memtest86+ image: /boot/memtest86+.bin
```

Anyone know what I can do now?

---

### Post by darkod on 2012-05-17
But it boots OK?

---

