---
title: "Problem with grub"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-08-20
I changed the partition I was booting from using grub setup, now that partition boots in verbose mode ie, it shows the loading process as if it were in recovery mode. Does anyone know how to turn this off?

---

### Post by tuxulin on 2008-08-20
read here [http://ubuntuforums.org/showthread.php?t=416604](http://ubuntuforums.org/showthread.php?t=416604)
i think in your case you need to add the the "splash" at the /vmlinuz lines

before editing the grub/menulist file please make a backup :)

hope it helps

Tuxulin

---

### Post by tuxulin on 2008-08-20
oopss

---

### Post by manishtech on 2008-08-21
> **tuxulin said:**
> read here [http://ubuntuforums.org/showthread.php?t=416604](http://ubuntuforums.org/showthread.php?t=416604)
i think in your case you need to add the the "splash" at the /vmlinuz lines

before editing the grub/menulist file please make a backup :)

hope it helps

Tuxulin
and **quiet** also along with **splash**

---

