---
title: "How to change grub?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by rfzz on 2007-11-26
I just recently installed ubuntu. I configured the os so that windows is the default os, but the grub/kernel and all that also shows up before booting into windows. 

How do I get rid of this message?

---

### Post by Hayden on 2007-11-26
If you mean the grub menu shows up before booting into windows, thats normal.

---

### Post by Ub1476 on 2007-11-26
```
gksudo gedit /boot/grub/menu.lst
```

Write that into the terminal. Now, what you want to edit is:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

When it looks like that for me, the menu is hidden and I have 2 seconds to show it.

Good luck:)

---

