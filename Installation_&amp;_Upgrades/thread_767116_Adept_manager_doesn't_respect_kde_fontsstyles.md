---
title: "Adept manager doesn't respect kde fonts/styles"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Mlehliw on 2008-04-25
I upgraded from 7.10 to 8.04. Things seem to work for the most part except Adept manager doesn't respect ANY settings that I use for the fonts or styles in kcontrol. It doesn't follow my Qt 4 settings either so I have no idea how it is deciding the style to follow.

Anyone else have this problem or suggestions on how to fix it?

---

### Post by MilitantPotato on 2008-04-25
You'll notice programs that need root access have the default color scheme.  This is easily fixed by running kdesudo kcontrol and choosing the fonts/colors/styles for the root account.  

Your account's colors are in /home/yourusername/.kde/share/apps/kdisplay/color-schemes/

Hope this helps.

---

