---
title: "Grub2 Menu - No timeout"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by steinaro on 2010-12-28
Hello All,

Can anyone tell me how I can setup the grub2 menu so that it does not timeout? What do I need to set in the configuration file? I did it once before on my old computer but forget now what I changed.

Thanks for the help.

---

### Post by steinaro on 2010-12-29
Anyone??

:popcorn:

---

### Post by garvinrick4 on 2010-12-29
```
gksudo gedit /etc/default/grub
```
change grub_timeout to -1
[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

---

### Post by steinaro on 2010-12-30
Thanks!

---

