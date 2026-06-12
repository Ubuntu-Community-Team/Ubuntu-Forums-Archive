---
title: "Need assistance with grub2 please."
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-07-16
Got jaunty on sda karmic on sdb. Was using this to boot karmic.
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title        SDB Karmic
configfile   (hd1,0)/boot/grub/menu.lst
```

This now fails as I reinstalled using todays daily build with ext4. I used advanced and told it to put grub on sdb1.

Whats the correct format for the configfile stanza.

---

### Post by dino99 on 2009-07-16
sudo update-grub2

---

### Post by philinux on 2009-07-16
> **dino99 said:**
> sudo update-grub2

Cant boot into karmic to try that. Hence the thread.

Any other suggestions.

I've tried

configfile   (hd1,0)/boot/grub/core.img
and
configfile   (hd1,0)/boot/grub/grub.cfg

I do get the grub prompt though.

---

### Post by philinux on 2009-07-16
Solved.
title        SDB Karmic
root (hd1,0)
chainloader +1

---

### Post by Gina on 2009-07-16
Ah, I see.  configfile only works when you have legacy grub for both systems.  That would explain why it wouldn't work for me.  Actually grub2 wouldn't boot a grub system either.  I installed a new Jaunty system to overwrite the grub2 main boot with legacy grub to access my original Jaunty system. So I've now got legacy grub multi-booting Karmic, Jaunty and other systems.

I'll have another go with grub2 when I get the time.

---

### Post by philinux on 2009-07-16
> **Gina said:**
> Ah, I see.  configfile only works when you have legacy grub for both systems.  That would explain why it wouldn't work for me.  Actually grub2 wouldn't boot a grub system either.  I installed a new Jaunty system to overwrite the grub2 main boot with legacy grub to access my original Jaunty system. So I've now got legacy grub multi-booting Karmic, Jaunty and other systems.

I'll have another go with grub2 when I get the time.

Righto. I got dropped into >grub when I used this.
configfile (hd1,0)/boot/grub/grub.cfg

I then remembered the chainloader and gave it a go.

---

