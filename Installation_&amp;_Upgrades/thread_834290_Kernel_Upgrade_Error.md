---
title: "Kernel Upgrade Error"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by djcrash1981 on 2008-06-19
Hi to all.


Today I've received an update notification i did the usual, click on the install button but for my surprise it failed.

Here's the error:
 Configurando linux-image-2.6.24-19-386 (2.6.24-19.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-386
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz


Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error al procesar linux-image-2.6.24-19-386 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
 linux-image-2.6.24-19-386

Now my question is? It's safe to boot my PC or there's a workaround to get this working??

I hope someone can help me.

Thanks for everything.

---

