---
title: "/etc/kernel-img.conf needs to be updated"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by buntu_hugenewbie11 on 2007-12-19
I am using Ubuntu Gutsy AMD64.
Today I ran apt-get upgrade and I got message in the terminal window which is shown below.
The thing is that I don't know if I should make these changes or not. Somebody please give me some direction.
Are the below changes vital? It seems like an outdated message as the file is written in 2006. 
With my latest upgrade I got the following statements:

Unpacking replacement linux-image-2.6.22-14-generic ...
Running postrm hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub/NEWS.Debian.gz

This file then said:
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

---

### Post by timseal on 2007-12-19
Yes, go ahead and change it.  It must be wrong because /sbin/update-grub is actually the script that produces that output (not the real update-grub).  So it must be wrong in the kernel-img.conf file.

---

