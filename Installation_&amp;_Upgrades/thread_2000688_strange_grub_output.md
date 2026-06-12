---
title: "strange grub output"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by luofeiyu on 2012-06-10
in my grub:
grub>set isofile="(hd0,msdos7)/tiger/debian.iso"
grub>$isofile
what i get is
unknow command '(hd0,msdos7)/tiger/d'

it's so strange thing ??

---

### Post by drs305 on 2012-06-10
I get the same result. It appears the set command may be character-length limited. I tried various names and it always cut off at the same point.

Not sure what you are trying to do, but the ISO links in my signature line might help you.

---

