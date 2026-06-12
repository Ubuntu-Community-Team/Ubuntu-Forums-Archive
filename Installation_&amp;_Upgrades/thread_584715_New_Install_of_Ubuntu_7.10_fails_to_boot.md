---
title: "New Install of Ubuntu 7.10 fails to boot"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-10-21
Downloaded Ubuntu 7.10 and booted it as a live CD. Clicked the install icon and the installation completed. 

I have a multiboot linux system and installed / on hda11 and /home on hda12. I do not install grub to the mbr and untick the option, I manually edit my  menu.lst with the new Ubuntu kernel and initrd.

On first boot, I receive the Ubuntu splash screen , but installation halts with
waiting for root filesystem.

The keyboard is active, but an alternate console shows no error messages and no further booting is possible??

Dont know if its a kernel or problem or my entry in menu.lst
However I have got around the problem using my self compiled 2.6.21 kernel and am now posting from Gutsy.

Extract from menu.lst

title Ubuntu 7.10
    kernel (hd0,10)/boot/vmlinuz root=/dev/hda11 vga=791 ro splash

vmlinuz is of course a symlink to my kernel-2,6,21 placed in boot on my ubuntu root,
I'm not usuing an initrd as my kernel has all the drivers necessary to start my rooot
filesystem (reiser) in other words reiser support is built into my kernel, not as a module.


Could someone who has installed Ubuntu 7.04 grub to their mbr show me the contents
of menu.lst

Thanks in advance.

---

