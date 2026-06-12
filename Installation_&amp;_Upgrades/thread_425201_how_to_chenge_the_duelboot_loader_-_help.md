---
title: "how to chenge the duelboot loader? - help?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by rami.arowesty on 2007-04-27
hi all.
i recently installed the ubuntu on my computer.
during the after i reboot the computer i found a new boot loader in my system.

the problem is that the ubuntu is the default operation system that loading.

how i can change it? i want the win XP will be the default operation system.

please help me.


Rami

---

### Post by NiN on 2007-04-27
Hit the <ctrl> and <F2> keys.
Type in the new window:
```
 gksudo gedit /boot/grub/menu.lst 
```

In the file opened there should somewhere be the text
```
 default    0
```

This selects the default entry to boot.

Search for "title" entrys and count them (starting at 0)

When you find your windows xp entry, replace the 0 after the "default" with the number you just counted.
(should be 2 in most cases)

thats all.

---

### Post by rami.arowesty on 2007-04-27
10x.

it worked.

---

