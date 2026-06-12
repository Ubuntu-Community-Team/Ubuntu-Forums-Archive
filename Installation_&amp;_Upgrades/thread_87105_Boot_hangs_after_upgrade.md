---
title: "Boot hangs after upgrade"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by coogor on 2005-11-07
Hi,

I managed to upgrade from 5.04 to 5.10 in several steps (apt-get dist-upgrade).
Now the problem is that the system does not boot properly: I shows someting like 
starting kernel 2.6.12..... and then the screen remains blank. nothing.
I tried dpkg-reconfigure grub and base-config, but that seems not to help....

any ideas?

TIA!
Coogor

---

### Post by jshein on 2005-11-07
O.K.

Questions first, as we need more information.

Motherboard & CPU
What exact kernel are you running? i386, i686 etc

Try pressing ESC t osee the brub boot menu, and booting into recovery mode for your kernel and see if that helps.

You could try booting from the Ubuntu cd, and installing a different kernel.

For example, I am running an AMD Turion laptop, and it performs much better with the i686 kernel than the default i383 ( caused lockups & higher power comsumption ) and the K7 kernel was just unusable for me.

---

### Post by coogor on 2005-11-07
[QUOTE=jshein]
Motherboard & CPU
What exact kernel are you running? i386, i686 etc
[/QUOTE]
It is a Pentium 233 MMX (IBM ThinkPad 770). I was running the 386 kernel, as it is a 586 machine. the 686 kernel would not be a good idea....

> 
Try pressing ESC t osee the brub boot menu, and booting into recovery mode for your kernel and see if that helps.

You could try booting from the Ubuntu cd, and installing a different kernel.


Well, I booted the SuSE 10.0 and from there the Ubuntu. I try to reinstall the linux-image-2.6.12-9-386 ....I'll keep you informed :-)

---

