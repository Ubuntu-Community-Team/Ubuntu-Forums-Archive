---
title: "Updating GRUB 2"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by rishabh_destiny on 2009-12-07
My grub is not upgraded. Each time I update to new linux headers, it just adds it to the menu list without deleting the previous ones.

This is the output when i run update-grub in the terminal.
> Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin


---

### Post by byStanderone on 2009-12-07
...hope this thread helps:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by rishabh_destiny on 2009-12-07
No help. According to the official Grub 2 wiki, the grub should automatically pick up the updates and delete the previous ones. Since the grub 2 is not having the menu.lst file, which I can edit manually, I don't know how to resolve the issue

---

### Post by rishabh_destiny on 2009-12-08
*bump*

---

### Post by rrcs on 2009-12-08
Use Synaptic to uninstall the old linux-image kernels :D

---

### Post by byStanderone on 2009-12-12
...grub2 doesn't have menu.lst, just : sudo update-grub and the configuration files with update itself.

---

### Post by QIII on 2009-12-12
As long as the kernel exists, GRUB2 will add it either when a new kernel is updated or when you run update-grub or update-grub2.

Remember that GRUB2 is a beta.

To remove older kernels from the GRUB list, you will need to remove the kernels themselves.  You can do that via Synaptic by searching on "linux-generic" and "linux-headers" and uninstalling the older ones.  Make SURE you are uninstalling the oldest ones.

However, I would recommend keeping at least the kernel prior to the one you intend to use, in case the newest kernel gives you problems.

You can edit some portions of what GRUB2 does using the 40_custom file and the like.  But you should read up on it first.  Do a forum search on "ranch hand".  He has done a lot of work and put together a great tutorial.

---

