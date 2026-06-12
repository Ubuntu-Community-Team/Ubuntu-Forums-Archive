---
title: "Ubuntu as 2nd boot on Gentoo linux machine"
date: 2006-02-23
forum: Installation &amp; Upgrades
---

### Post by thomasp on 2006-02-23
Hi everyone,

I currently have a machine running gentoo linux, 3 partitions (/boot, /swap, /) fill the whole drive. I want to give ubuntu a go, keeping gentoo up to date takes quite a lot of my evenings... It is however a very stable system, so I don't want to install ubuntu over it, not to mention 5GB of data I'd have to backup to CD.

Can I install ubuntu to /ubuntu, and have the ubuntu installer add a boot option to my current lilo config? The /boot partition is ext2, and / is reiser4.

Option 2 :???: is to buy a second hdd...

Much thanks,
thomasp

---

### Post by taurus on 2006-02-23
I have Ubuntu on the first HD and Gentoo on the second and GRUB (from Gentoo) can boot both!  If you don't want to mess around with your data on Gentoo's and can afford it, get a second HD and connect it as a slave drive.  Then, install Ubuntu on it and everybody is happy...  ;)

---

