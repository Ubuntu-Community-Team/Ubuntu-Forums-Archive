---
title: "Dual booting Ubuntu 12.04 using Windows boot loader"
date: 2012-08-27
forum: Installation &amp; Upgrades
---

### Post by jibawakee on 2012-08-27
I want to install ubuntu but i want it to be like a wubi boot loader

---

### Post by darkod on 2012-08-27
That is not recommended since grub2 does not fit on the partition boot sector. It will have to save part of it inside the partition and during updates this location can change making it impossible to boot until you reinstall grub2.

Unless there is a really important reason it's better to install it on the MBR.

If you really, really need to use windows bootloader, install grub2 on the root partition and then add it to windows bootloader. Usually EasyBCD is used for that but I don't use it and don't know any details about that.

---

### Post by jibawakee on 2012-08-27
Thanks

---

