---
title: "Install Ubuntu but not Grub?"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by cmulax on 2007-03-01
So I have been multibooting for some time now (mostly multiple ubuntus, since windows and gentoo just dont work (actually i think gentoo would it just takes too much time that i dont have now...)), and i just wanted to know if there was a way to install ubuntu without installing grub.  Essentially i want to manage the grub in my primary ubuntu installation and not have to worry about any others overriding it.

ive heard something about an alternate install cd, but no clear ways of going about doing this.  any help would be much appreciated!

---

### Post by louieb on 2007-03-01
Yea it works out pretty slick. When you install the 2nd Linux distro  have it install GRUB on the MBR of the install partition. The Ubuntu live CD on the page with the install button there is a place to tell it to install GRUB.  Its hidden well but look for [COLOR=Blue](hd0)[/COLOR] and click on it and change it to (hd0,?) ? being the 2nd distro's install partition. Then to use it: 
Add a configfile entry in the first Linux's menu.lst file. 
The Dual Boot link in my signature describes this method and the chainloader method  of dual,triple ...  booting multiple distros on the same PC.
Have fun.
Louis.

---

### Post by cmulax on 2007-03-01
ok thank you very much :)

i will try that and see if any issues come up.  i was just getting annoyed that every time i installed a new distro, it would use that grub and i just wanted to use the grub from my primary (stable) ubuntu.

---

### Post by ssican on 2007-03-01
cmulax, see this alternatives : [http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html](http://www.hezardastan.org/breezy_xp_dualboot/en/gaginstall.html)   and   [http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

---

