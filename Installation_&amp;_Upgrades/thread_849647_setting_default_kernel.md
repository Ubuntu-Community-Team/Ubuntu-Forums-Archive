---
title: "setting default kernel"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by Richard-g8jvm on 2008-07-04
Hi
where is the boot behaviour settings, ie to reduce the kernel listing at boot up and to select the default kernel

thanks 
Richard

---

### Post by Pumalite on 2008-07-04
Edit menu.lst and comment out the kernels you do not want to show up in the Grub menu.

---

### Post by Richard-g8jvm on 2008-07-04
Ok I've just had a look at /boot/grub/menu.lst.

There's no kernels listed there, where is the automagic list generated


Richard

---

