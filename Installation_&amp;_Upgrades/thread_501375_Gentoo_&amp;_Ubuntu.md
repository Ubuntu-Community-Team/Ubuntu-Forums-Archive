---
title: "Gentoo &amp; Ubuntu"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by Sean-Der on 2007-07-15
I have had Gentoo for a long time and would like to install Ubuntu because it is more stable but I have a few questions first

Is it possible not to install GRUB with Ubuntu and just add it to my menu.lst on my /boot partiton latter and what would I add?

Can I use my existing home folder from my Gentoo install it is on my / partition though that is the only problem if so tell me how? 

Thank You

---

### Post by Pumalite on 2007-07-15
You would have to change the letters according to your set up, but here is an example:

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=88c18a5f-a342-4a80-8bd3-45942765da58 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

I don't know if you can use your existing home folder.
Good luck.

---

### Post by Sean-Der on 2007-07-15
Thank you for the speedy reply and I ended up re partioning my / to make a /home partition

---

