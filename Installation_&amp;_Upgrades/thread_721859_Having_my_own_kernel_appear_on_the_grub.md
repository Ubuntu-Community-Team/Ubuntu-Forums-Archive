---
title: "Having my own kernel appear on the grub"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2008-03-11
Hi i am trying to make some changes in the kernel code, but before I do that I want to manually compile the kernel and make it appear on the grub so that i can fall back to the stable kernel if there is a problem. Can someone let me know how to do it?

---

### Post by ittiam on 2008-03-11
I am following this how to [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

it says after ```
make menuconfig
``` 
and
 ```
make-kpkg --rootcmd fakeroot --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```, 

you would find packages generated in ~/. But i did not find any.

---

### Post by tgalati4 on 2008-03-11
Copy your new kernel and initrd to /boot.  Edit /boot/grub/menu.lst and add the appropriate boot entries.  Just duplicate an existing boot entry and then edit it for the appropriate kernel name.

---

