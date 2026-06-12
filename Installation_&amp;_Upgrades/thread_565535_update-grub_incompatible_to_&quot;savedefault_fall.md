---
title: "update-grub incompatible to &quot;savedefault fallback&quot;?"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by nil0z on 2007-10-02
Hi,

i try to configure a fallback installation into a server's grub, see [grub manual]("http://www.gnu.org/software/grub/manual/html_node/Booting-fallback-systems.html"). So the menu.lst has to look like this:

```
default saved
fallback 0
timeout 10
 
title Fallback Ubuntu
  root (hd0,0)
  kernel /boot/fallback/kernel
  initrd /boot/fallback/initrd
  savedefault

### BEGIN AUTOMAGIC KERNELS LIST
# ...

title Ubuntu, kernel 2.6.20-16-generic
  root (hd0,0)
  kernel /vmlinuz-2.6.20-16-generic root=/dev/mapper/Ubuntu-edgy ro
  initrd /initrd.img-2.6.20-16-generic
  ***savedefault fallback***

### END DEBIAN AUTOMAGIC KERNELS LIST
```
The command ```
grub-set-default 1
``` triggers the kernel #1 (ubuntu standard kernel) on reboot. If this command is not repeated then, after a second reboot grub boots the fallback kernel #0.

Unfortunatly, ***update-grub*** (which is run on each kernel update) writes ***savedefault*** instead of ***savedefault fallback*** into the menu.lst. How do i correct this?

nil0z

---

