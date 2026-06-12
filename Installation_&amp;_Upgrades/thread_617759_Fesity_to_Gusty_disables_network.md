---
title: "Fesity to Gusty disables network"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by berck on 2007-11-19
I upgraded from Feisty to Gusty recently using a Dell 530n which came with Feisty. After the upgrade process finished, I was asked to reboot. Upon doing so, I no longer have eth0 available. Says it can't find it at all. When I did an lshw -C network, it reported that the card wasn't used or attached.

So, I decided to change kernels and boot one of the other ones. I was booting into kerenl 2.6.22-14-386. Now I changed to 2.6.22-14-generic. After the change, the network works just fine. My lshw command comes back that it loaded driver 'e1000-ich9' for the network card.

What's the deal with the standard kernel and how can I get this fixed?

EDIT:
I also have the same problem with sound. The driver loads with the generic kernel but not the 386 kernel

---

### Post by Pumalite on 2007-11-19
Boot back into -386 and try this:
sudo apt-get install linux-backports-modules-generic
(as an aside; I think is better to stick to generic)

---

### Post by berck on 2007-11-20
Looks like the issue was not turning off the restricted drivers before I did the update. I just tried it on another system and things went smooth.

---

