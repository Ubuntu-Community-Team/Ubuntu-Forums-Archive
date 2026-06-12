---
title: "[SOLVED] Ubuntu &amp;amp; Mint"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by rfruth on 2007-01-15
I have Edgy installed no problem then I installed Mint on a different partition still no problem but now when grub starts Mint is the default I want Ubuntu as the default, does menu.lst control that and if so how should it be changed ?

---

### Post by loell on 2007-01-15
in menu.lst there is

```


## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
# default	 saved



```

uncomment the 

```
default save
```

that way, the item you selected when you first boot will be your default, so when you can interchange easily your default by just selecting during boot.

---

