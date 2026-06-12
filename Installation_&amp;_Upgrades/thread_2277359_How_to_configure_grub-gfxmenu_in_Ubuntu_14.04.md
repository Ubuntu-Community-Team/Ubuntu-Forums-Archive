---
title: "How to configure grub-gfxmenu in Ubuntu 14.04?"
date: 2015-05-08
forum: Installation &amp; Upgrades
---

### Post by antonio922 on 2015-05-08
Hello,

How can I configure a boot menu with background image like package grub-gfxmenu, with grub2? If I am right, grub-gfxmenu is only available with grub legacy, and that cannot be installed with Ubuntu 14.04.

Thanks!

---

### Post by ubfan1 on 2015-05-08
Try putting your background image into /boot/grub named splash.png.  Then rerun
sudo update-grub
and see if you now have the image on the grub menu background.

---

