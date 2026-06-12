---
title: "setting the default boot choice?"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by RunsWithScissors on 2006-09-11
how do I set what the default is in the boot list?
I have about 4 thing there. there are different kernls and things as well as other OS. How do I set what is the default.

---

### Post by ape on 2006-09-11
Edit your /boot/grub/menu.lst file and look for the following section:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default         0
```

You will want to change the 'default' number to the entry that you want to be the default choice on bootup.

---

