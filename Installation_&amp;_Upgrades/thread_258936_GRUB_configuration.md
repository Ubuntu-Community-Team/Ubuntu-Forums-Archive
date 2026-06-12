---
title: "GRUB configuration"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by spock2263 on 2006-09-16
Hello guys!
How can I change the default OS in GRUB and how can I make it not to have a timeout? Generally, how can I make any changes to GRUB?
Thanks a lot!

---

### Post by whizbaby on 2006-09-16
You can do what you want by editing your */boot/grub/menu.lst* (e.g. **sudo nano */boot/grub/menu.lst***), at the beginning of it is a manual.

---

### Post by Iarwain ben-adar on 2006-09-16
Hiya,
could you post your menu.list here?

Basicly you just have to change this
```
default		0
```

to the number your other OS has (count the entry's, starting from 0)


Iarwain

---

### Post by spock2263 on 2006-09-16
Thanks a lot guys!!

---

