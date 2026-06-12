---
title: "installer with 2.6.11 kernel"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by gny on 2005-04-11
Hello,

I'm looking for an installer with 2.6.11 kernel. I think i have tried everything. Thing is my Sata controller _ONLY_ works under 2.6.11. It's an Promise 150 TX4. If i start knoppix 3.8 which has 2.6.11 i can use the controller, how ever I have had problem after debotstrap to make my system booteble with grub os lilo. I whant to set up an softraid which complicates things some.

So where can i find an ubuntu, or debian install cd whith 2.6.11?  I really, really need it. My other harddisk has crashed, so I'm sort of out of options.

---

### Post by skrat on 2005-04-11
IMHO that doesn't depend on kernel version, more on modules, compiled with kernel. Promise 150 TX4 works also with older kernels (I am sure that it works with customly compiled 2.6.8.1), the only problem is to find installation, which has kernel with this support included  :roll:

---

### Post by az on 2005-04-11
Have you tried Hoary?  If it does not work, wait for the first Breezy beta (alpha)

---

### Post by gny on 2005-04-11
Japp, tried hoary. 

On kernel.org:

[http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.11](http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.11)

The suport for Promise 150 TX4, where just added to the 2.6.11 kernel.
So the hoary installer does not find my sata controller.

There is a promise sata module in 2.6.8 as well, but it does not suport the TX4  :???: 

I have managed to boot knoppix, make softraid array and debootstrap it. but have some trouble with lilo. Think i figured it out. 

Would be so much easy with an installer with 2.6.11 kernel.

---

