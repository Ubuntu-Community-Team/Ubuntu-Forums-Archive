---
title: "Net install needs RTL8150"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by gratch6 on 2006-12-03
Installing Edgy on an old laptop with PCMIA card CD rom (not recognized and BIOS would not allow boot anyway), floppy works, no internal network card so the network card is USB - linksys USB100m which I know will work with RTL8150. I am installing with grub for DOS using a net install from:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)
which does not have the rtl8150 module (fatal error on modprobe - module not present). 

Floppy boots to dos, grub runs, kernel loads but initial install fails at network setup due to the absence of this module. 

I need some help to get past this point. Is there some way to get the module into the kernel?

](*,)

---

