---
title: "getting an error since updated i686"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by pdk001 on 2005-05-13
since i've updated i686 last day, grub is getting an error
i have to hit " windows" first and hit "microsoft windows xp professional" is work fine

following options are the part of the menu.lst file

title windows
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0) +1

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

any ideas?

---

