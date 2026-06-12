---
title: "Updated server from 10.04 to 12.04. Still boot from old kernel"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2012-08-24
I have just finished a succesfully upgrade from 10.04.4 to 12.04.1 on my remote server. After reboot, I have verified that it is still booting from the old kernel:

[FONT="Courier New"]$ uname -a
Linux socrates 2.6.32-41-generic-pae #94-Ubuntu SMP Fri Jul 6 17:08:20 UTC 2012 i686 i686 i386 GNU/Linux
I have also run update-grub:[/FONT]

[FONT="Courier New"] $ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.2.0-29-generic-pae
Found kernel: /boot/vmlinuz-2.6.32-41-generic-pae
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done[/FONT]

But it is still booting from the old one... I have verified that I am still running grub Legacy:

 [FONT="Courier New"]  dpkg -l grub* | grep ii
ii  grub                                 0.97-29ubuntu66                     GRand Unified Bootloader (Legacy version)
ii  grub-common                          1.99-21ubuntu3.1                    GRand Unified Bootloader (common files)[/FONT]

Thihs is a remote headless server, and I only have ssh access. I don't want to miss it while playing with grub!

---

