---
title: "Aurora themes installation"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by davbren on 2007-11-19
Hey, I'm trying to install the Aurora theme engine which requires the latest GTK+ 2.x the problem is I have to install an updated glib too, this is a pain, I've done the whole ./configure thingy which is all very well and good but in the synaptic it still says glib 2.14 which is useless for me. When I go to uninstall it to then reinstall the new one it tells me I'm about to uninstall a whole loada stuff i really need and its tons of stuff!

Really need help on this one.

---

### Post by abrichr on 2007-11-19
In a terminal, type:

```
sudo apt-get install libgtk2.0-dev
```

Then try to compile.

---

### Post by davbren on 2007-11-20
But that'll install the wrong version won't it? I need a version gtk+2.2 something something.

also I can't uninstall the current version without uninstalling a whole load of other stuff that i really need.

---

