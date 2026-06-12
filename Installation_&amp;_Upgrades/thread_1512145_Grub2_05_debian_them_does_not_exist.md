---
title: "Grub2 05_debian_them does not exist"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Micano on 2010-06-17
Hey,

In etc/grub I don't have 05_debian_theme, but I do have it in grub.d.old. 

Because I'm such a huge noob I don't want to **** anything up, but  I want to be able to change theme. 

Please help.

Thanks!

---

### Post by plucky on 2010-06-18
> **Micano said:**
> Hey,

In etc/grub I don't have 05_debian_theme, but I do have it in grub.d.old. 

Because I'm such a huge noob I don't want to **** anything up, but  I want to be able to change theme. 

Please help.

Thanks!

It is not /ect/grub/ it is /etc/grub.d/

From a terminal ```
gksudo gedit /etc/grub.d/05_debian_theme
``` to edit the file.

Good Luck

---

