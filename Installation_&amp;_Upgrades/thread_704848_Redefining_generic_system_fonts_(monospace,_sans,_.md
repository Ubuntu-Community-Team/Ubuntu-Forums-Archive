---
title: "Redefining generic system fonts (monospace, sans, serif, etc.)?"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by duesen on 2008-02-22
How do I specify which fonts correspond to generic fonts in Ubuntu? (serif, sans, monospace, etc.)

if you go to System > Preferences > Appearance > Fonts, you will see that there are generic font names available in the font list: Sans, Monospace, Serif. Similarly, in Firefox font settings (Edit > Preferences > Content > Font & Colors) you will see similar generic names.

These names are not real font names, but rather generic aliases. How do I know which actual fonts are being used in their place? How do I change these assignments?

Thanks!

---

### Post by spiderbatdad on 2008-02-22
check out the /etc/fonts directory for conf.avail  and conf.d

---

### Post by duesen on 2008-02-22
> **spiderbatdad said:**
> check out the /etc/fonts directory for conf.avail  and conf.d

I found a couple of files there that looked promising:
[FONT="Courier New"]
/etc/fonts/conf.d/40-generic.conf
/etc/fonts/conf.d/69-unifont.conf[/FONT]

Changed the first one by commenting out first lines in each section. Rebooted, no difference...

Any further information?

Thanks!

---

