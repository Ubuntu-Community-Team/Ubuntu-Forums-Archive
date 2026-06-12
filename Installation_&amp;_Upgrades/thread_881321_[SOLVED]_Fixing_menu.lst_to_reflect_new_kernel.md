---
title: "[SOLVED] Fixing menu.lst to reflect new kernel"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by Dennis N on 2008-08-05
New to Ubuntu. When the kernel was updated to 2.6.24-19 on my machine, a message appeared asking if I wanted a new menu.lst to be written, or keep the old one. The default choice was "keep the old one", and using the maxim "when in doubt, use the default" I clicked forward. I now see that that was the wrong choice as the new kernel is not entered on menu.lst, so I am still booting up with 24-16. (This was part of the first update on a new machine, so I suppose 24-17 and 24-18 were already old). It is however shown as installed by the package manager, and is sitting in /boot/grub.

My question is how to get menu.lst updated to the newer kernel?

Thanks for advice,
Dennis N.

---

### Post by lisati on 2008-08-05
From the terminal (Accesories->terminal), try ```
sudo update-grub
``` and let us know how you get on.

---

### Post by Dennis N on 2008-08-05
Thanks - the menu.lst updated sucessfully - will test on next startup.

---

