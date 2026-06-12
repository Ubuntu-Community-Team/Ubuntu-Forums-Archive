---
title: "installing conky: Could not find XdbeQueryExtension in -lXext"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by computerguy23 on 2010-11-15
I have already checked for updates. What do I need to get this? Thanks.

---

### Post by dino99 on 2010-11-15
why conky ?

---

### Post by computerguy23 on 2010-11-15
I haven't found any alternatives.

---

### Post by dino99 on 2010-11-15
> **computerguy23 said:**
> I haven't found any alternatives.

torsmo, gdesklets, superkaramba (kde)

[http://kyleabaker.com/2010/03/30/want-cool-desktop-stats-conky/](http://kyleabaker.com/2010/03/30/want-cool-desktop-stats-conky/)

[http://torsmo.sourceforge.net/](http://torsmo.sourceforge.net/)

searching "panel" into synaptic will give you some more packages too

---

### Post by computerguy23 on 2010-11-15
Thanks. I'm going to look into those. I finally got it working though by installing several extra libraries following hours of reading. 

91  sudo apt-get install libx11-dev
102  sudo apt-get install libxext-dev
115  sudo apt-get install libxdamage-dev libglib2.0-dev

---

