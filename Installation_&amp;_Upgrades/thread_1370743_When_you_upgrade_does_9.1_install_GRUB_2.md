---
title: "When you upgrade does 9.1 install GRUB 2?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by kjb34 on 2010-01-02
I was curious because it seems like my bootloader is GRUB legacy. I try to use this command gksudo gedit /boot/grub.cfg and etc/default/grub they are empty. It's not a big deal I'm just curious. If is not do I need to change to GRUB2?

---

### Post by mick222 on 2010-01-02
If you upgrade grub stays as grub-legacy ,and the filesystem stays as ext3 if you want grub2 you can install it but for ext4 you will need to reinstall.I'd leave things if your happy as they are.

---

### Post by kjb34 on 2010-01-02
Ok I thought so. I'm happy with GRUB. Thank you for clearing things up

---

