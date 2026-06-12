---
title: "Upgraded from 6.06 to 6.10, apt keeps trying to update grub"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by garyozzy on 2007-02-24
I installed Ubuntu 6.06 on my Macbook today. I did the triple boot with lilo thing. I did not use grub. When I upgraded to 6.10, grub tried to install and now whenever I run apt, it asks me about grub and then throws errors. Can I somehow get apt to stop trying to install grub and another package called ubiquity (or something like that)?

now apt-get  shows this error:

```
Setting up grub (0.97-11ubuntu14) ...
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

dpkg: error processing grub (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on grub; however:
  Package grub is not configured yet.
dpkg: error processing ubiquity (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub
 ubiquity


```

thanks

gary

---

### Post by NosLycn on 2007-02-24
I can't say I have much experience with Ubuntu and lilo (although I have used it on my Debian/Sarge box).  Is it possible to apt-get remove grub ?  If you can do that, seeing as you don't use grub, you would theoretically have no reprocussions and it (hopefully) wouldn't make you install it again.

---

### Post by garyozzy on 2007-02-25
aha! it works. i haven't rebooted yet so I don't know whether I can still boot into ubuntu but now apt doesn't throw errors


thank you

---

