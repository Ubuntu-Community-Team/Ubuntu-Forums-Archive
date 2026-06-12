---
title: "What partition have the installed netbook remix 9.1?"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by losi on 2010-01-03
hi all,
like to know ow can check the intsalled program what partition has.
How can i know it? 
thanks.
losi

---

### Post by raymondh on 2010-01-03
Losi ....

From GRUB, select and boot UNR.  For a few seconds, it will show GRUB booting from [COLOR="Red"]hd0,5[/COLOR] (as an example).

Another way is to access a terminal and type

```
sudo fdisk -l
```

The output will show you your partition table.

---

