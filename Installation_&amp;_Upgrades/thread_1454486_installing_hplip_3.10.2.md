---
title: "installing hplip 3.10.2"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by desertfox3 on 2010-04-14
travis@travis-desktop:~$ sh hplip-3.10.2.run
sh: Can't open hplip-3.10.2.run
travis@travis-desktop:~$ 


this is the message when i try to install....does anyone know what i'm doing wrong? i followed the directions on the hp site for linux.

---

### Post by xangelux on 2010-04-15
You need to change the permit to execute

$ sudo chmod a+x hplip-3.10.2.run

And then you can run it.

---

