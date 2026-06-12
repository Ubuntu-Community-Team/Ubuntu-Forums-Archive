---
title: "Odd GURB problem..."
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Leo_01 on 2006-03-13
Every time i update the kernal i notice that grub "deletes" the "link" to my Win XP on my dual booting system...
It is not a big problem for me to restore the "link" but kind of odd...
is there something wrong with grub?

---

### Post by Dullin on 2006-03-13
I found that it behaved this way only when I installed Windows after Ubuntu.

Of course a reinstall is not really a way to fix your problem so I would make a bug report about it.

---

### Post by lha on 2006-03-13
Have you placed your Windows links between
```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
```
and
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```? If yes, there's your reason. Place your own entries before or after those lines, not between them.

---

### Post by Leo_01 on 2006-03-13
No wonder!
Tks!

---

