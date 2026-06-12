---
title: "upgraded feisty and lost xp from grub"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by andytof47 on 2007-04-23
Hi I just Installed Feisty from a beta disk I had and then ran an update 

Everything went well just lost my XP entry from the Grub menu


Any ideas how to get this one back?

:confused:

---

### Post by andytof47 on 2007-04-23
bump............................Please

---

### Post by icechen1 on 2007-04-23
ok it is
Code:

sudo gedit /boot/grub/menu.lst

tape that in the terminal
and add on the bottom:
```
title		Microsoft Windows XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
[COLOR="Red"]By (hd0,0) you have to fill in your hard disk and you partition. Begin to count with zero!
If you have Windows installed on you 3rd hard disk second partion it becomes: (hd2,1), got it?[/COLOR]
you might use GPARTED to know where is your XP partitition.

---

### Post by andytof47 on 2007-04-23
Cheers

Have to make a backup next time I upgrade - just wasn't a problem with edgy


Cheers

---

