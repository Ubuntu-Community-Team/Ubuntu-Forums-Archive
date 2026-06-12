---
title: "linux-image-2.6.32-22-generic update freeze"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by StiveG on 2010-06-03
When I try to update my 2.6.32-21 kernel to the new one (2.6.32-22) the update process freeze right after :

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.32-19-generic
Found initrd image: /boot/initrd.img-2.6.32-19-generic
Found memtest86+ image: /boot/memtest86+.bin

<---- Everything freeze here, before the "done" ---->

So I have to manualy stop it.

My kernel is not fully update, so I can't uninstall it.

Pretty stuck...

Anyone has any idea how to solve this? Would be really appreciate!

Thanks

Steve


**SOLVE**

SOLVE :

Restart.
Choose 2.6.32-22 (recovery mode)
Repair broken packages
Update grub bootloader
Resume normal boot

- You will be at the command line at this point.

Reboot

Everything should be ok.

---

