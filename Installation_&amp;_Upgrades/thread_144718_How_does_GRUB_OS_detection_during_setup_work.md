---
title: "How does GRUB OS detection during setup work?"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by timelord726 on 2006-03-14
Hi everyone!

How does the GRUB operating system detection thing work in Ubuntu setup?  When installation is about to finish, it prepares to install GRUB to the MBR, but it is able to scan your computer and detect other operating systems and automatically generate an appropriate menu.lst to include those as boot options.  My real question is this -- is there any way to do something similar after Ubuntu has already been installed?  For example, if I add another operating system to my computer, can I rerun that cool little auto-detection program somehow and let it rewrite my GRUB configuration for me?

Thanks very much!

---

### Post by o_fortuna on 2006-03-14
[QUOTE=timelord726]Hi everyone!

How does the GRUB operating system detection thing work in Ubuntu setup?  When installation is about to finish, it prepares to install GRUB to the MBR, but it is able to scan your computer and detect other operating systems and automatically generate an appropriate menu.lst to include those as boot options.  My real question is this -- is there any way to do something similar after Ubuntu has already been installed?  For example, if I add another operating system to my computer, can I rerun that cool little auto-detection program somehow and let it rewrite my GRUB configuration for me?

Thanks very much![/QUOTE]
I honestly don't know if this will work -- but
```
sudo update-grub
```
seems right.

If that doesn't work, you can always add it yourself to the /boot/grub/menu.lst file. That's a bit more complicated, though.

---

