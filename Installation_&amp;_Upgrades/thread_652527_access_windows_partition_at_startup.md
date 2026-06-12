---
title: "access windows partition at startup"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by querulousennui on 2007-12-28
Hi, I've recently installed Ubuntu (my first try at Linux). When installing, I made put the slider on 50% windows xp and 50% ubuntu. However, at startup when I hit 'esc' to choose which os to boot, windows is not there. How do I make it appear there to boot in windows instead of ubuntu?


Thanks

---

### Post by Pumalite on 2007-12-28
Do you see the Grub menu?

---

### Post by forestpixie on 2007-12-28
and if you do and win is missing in action what does this from a terminal give you (applications >accessories >terminal)

```
sudo fdisk -l
```

---

### Post by querulousennui on 2007-12-29
yes, i use the grub menu. thanks for your help, i fixed it tonight. all i did was update from 7.04 (my installer cd) to 7.10 and windows appeared in the grub menu. yay!

---

