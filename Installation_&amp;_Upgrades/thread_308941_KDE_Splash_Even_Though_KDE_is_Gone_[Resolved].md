---
title: "KDE Splash Even Though KDE is Gone [Resolved]"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by Recked on 2006-11-28
Hey,

I just installed kubuntu-desktop via aptitude as I wanted to take a look at KDE. I played around a bit and decided at least for my laptop I would stick with Gnome. Problem is after removing kubuntu-desktop via aptitude I still have the KDE/Kubuntu splash screen when the OS is booting up.

Is there some way to get back to the Gnome boot splash?

thank you

---

### Post by aysiu on 2006-11-28
Try this:
[http://doc.gwos.org/index.php/Different_usplash](http://doc.gwos.org/index.php/Different_usplash)

---

### Post by Recked on 2006-11-28
Thanks.

I tried it but it appears to have had some issue at least with the first command....

dlaptop@dlaptop:~$  sudo update-alternatives --config usplash-artwork.so
Password:

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.
dlaptop@dlaptop:~$  sudo dpkg-reconfigure linux-image-`uname -r`
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by Recked on 2006-11-28
That worked after all.

I rebooted/restarted the laptop and I'm back to where I was before trying KDE.

Thanks a lot for the help Aysiu

:-D

---

### Post by Ubuntu Joe on 2007-01-24
Nice job fellas . . .

=D>

---

