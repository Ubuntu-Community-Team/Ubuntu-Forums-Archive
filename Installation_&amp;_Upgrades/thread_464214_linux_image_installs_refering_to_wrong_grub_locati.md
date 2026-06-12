---
title: "linux image installs refering to wrong grub location"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-06-04
I noticed that since the few last updates I did, I see this re-occuring message that indicate the linux image install is looking at a wrong grub path location It eventualy searches for it and finds it but still, it is a bug.


***** I copied it by hand so there might be typos in it *****

Seting up linux-image-2.6.20-16-generic (2.6.20-16.28) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
[B]Running postinst hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead [/B]!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-generic
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done




P.S.: tried to report bug  but launchpad says its offline !!!

---

### Post by nick623 on 2007-06-10
I'm running Feisty. I'm getting the same message when I update.
I believe it says to refer to /usr/share/doc/grub/NEWS.Debian.gz which reads:

grub (0.97-16) unstable; urgency=low

  grub-install and update-grub has changed location.
  
  There's a wrapper available in /sbin to keep backward compatibility but
  it'll be removed once Etch is release as stable. You _must_ edit your
  /etc/kernel-img.conf and change the paths to /usr/sbin/update-grub. 
  For example:

  ,----[ /etc/kernel-img.conf ]
  | ...
  | postinst_hook = /sbin/update-grub
  | postrm_hook   = /sbin/update-grub
  `----

  Should be change to:
  
  ,----[ /etc/kernel-img.conf ]
  | ...
  | postinst_hook = /usr/sbin/update-grub
  | postrm_hook   = /usr/sbin/update-grub
  `----

 -- Otavio Salvador <otavio@debian.org>  Thu, 14 Sep 2006 23:25:36 -0300


I thought this might have been a result from upgrading to Feisty from Edgy.  But now I don't think so.

---

