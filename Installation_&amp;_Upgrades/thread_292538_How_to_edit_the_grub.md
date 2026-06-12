---
title: "How to edit the grub"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Kemfisee on 2006-11-04
I need help with a duel boot with XP and UBUNTU,,

Can someone tell me how to edit my Grub so i can make XP the default OS to load first instead of UBUNTO...

What do i change in the /boot/grub/menu.lst file to make XP boot first after the timeout!!!!!

thanks

KEMFISEE

---

### Post by dcstar on 2006-11-04
> **Kemfisee said:**
> I need help with a duel boot with XP and UBUNTU,,

Can someone tell me how to edit my Grub so i can make XP the default OS to load first instead of UBUNTO...

What do i change in the /boot/grub/menu.lst file to make XP boot first after the timeout!!!!!

thanks

KEMFISEE

Did you see this at the start of that file:
```
## default num
# **Set the default entry to the entry number NUM**. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
**default**		0
```

---

