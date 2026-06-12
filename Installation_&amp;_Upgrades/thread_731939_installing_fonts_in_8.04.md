---
title: "installing fonts in 8.04"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by haed on 2008-03-22
hi,
i can't install fonts on 8.04

nautilus report an error: can't show/manage fonts:/// positions 

copy and paste ttf file in /usr/local/share/fonts or /usr/share/fonts/truetype/ is not possibile because ... paste is not enabled (but pasting on desktop or everywhere is possible)

sudo cp ... give no errors and ttf file is in fonts folder but open office (or others programs) doesn't use that font (neither after a fc-cache -f -v)

what's appened?

p.s.: it's a 8.04 clean installation

p.p.s.: on 7.10 everything works fine

---

### Post by haed on 2008-03-22
it's seems to work

i create a .fonts folder in home folder, copying ttf file in .fonts folder and restarting session

---

