---
title: "/etc/kernel-img.conf : changing update-grub path?"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Claire on 2007-04-14
I'm not sure if this is just me, but I've noticed an odd issue with my update-grub script when I downloaded the newest kernel.  When I tried to configure it from the terminal, it put out an error;

Setting up linux-image-2.6.20-15-generic (2.6.20-15.25) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-15-generic
Could not find postinst hook script [usr/sbin/update-grub].
Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
dpkg: error processing linux-image-2.6.20-15-generic (--configure):
 subprocess post-installation script returned error exit status 2

Which is really odd considering I have update-grub both at /usr/sbin/update-grub and /sbin/update-grub.  When I edited the /etc/kernel-img.conf file from

postinst_hook = /usr/sbin/update-grub
postrm_hook   = /usr/sbin/update-grub

to

postinst_hook = /sbin/update-grub
postrm_hook   = /sbin/update-grub

then everything configured fine, but it told me

Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz

You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Is this going to cause issues in the future?  Should I edit the /etc/kernel-img.conf file back (even though when it had /usr/sbin/update-grub, it somehow couldn't find the script)?  And has this been a common problem?

---

