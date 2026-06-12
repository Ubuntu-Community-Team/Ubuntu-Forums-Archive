---
title: "install over a dual system disk"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by josquin on 2005-10-22
HI FOLKS!

in my pc there are debian sarge and win XP, a dual booting system with lilo.

I would like to install ubuntu over the debian partition on my hard disk. and possibly left win untouched.

Is there any raccomandations to follow? is there any know issue for such a configurations? is it enough to run the installation cd and telling the installer to overwrite the debian partion? (of course everything has been backed up)) will i still have my lilo allowing me to run win?

thanks, i have browsed the forum without luck.

---

### Post by jasmuz on 2005-10-22
Howdy!

Just install as normall, and choose the install partition to where you have the Debian Sarge, and leave it to work, then afterwards it will remove Lilo and install GRUB, allowing you to boot Windows without any problem.

---

