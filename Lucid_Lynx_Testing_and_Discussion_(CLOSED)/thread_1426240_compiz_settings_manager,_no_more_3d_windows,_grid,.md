---
title: "compiz settings manager, no more 3d windows, grid, etc?"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by switch10 on 2010-03-10
I am messing with the alpha 3 release of 10.04.  I installed compiz settings manager, and noticed a few things are missing.  Most notably, grid, and 3d windows.

---

### Post by Post Monkeh on 2010-03-10
> **switch10 said:**
> I am messing with the **alpha 3** release of 10.04.  I installed compiz settings manager, and noticed a few things are missing.  Most notably, grid, and 3d windows.

i'd guess that could be your problem right there

---

### Post by overdrank on 2010-03-10
Moved to Lucid Lynx Testing and Discussion

---

### Post by Nightstrike2009 on 2010-03-10
I have also noticed this problem also "Horizontal Virtual Size" will not set to 4 again (as it did in a long previous distro) so 3D cube effect is currently impossible, 3D triangle or pentagon however is ok (reflection effects also missing).

---

### Post by Keyper7 on 2010-03-10
> **switch10 said:**
> I am messing with the alpha 3 release of 10.04.  I installed compiz settings manager, and noticed a few things are missing.  Most notably, grid, and 3d windows.

Do you have the package **compiz-fusion-plugins-extra** installed?

---

### Post by Nightstrike2009 on 2010-03-10
Probably not thanks keeper

Found a way to get cube working click workspace switcher on bottom panel>preferences>set columns to 4, this works on mine anyhow.

if you have removed it (i have a dock bar) do this;

In terminal type these commands:

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

Both panels should reappear make your changes then delete bottom panel again if you have a dockbar

---

### Post by Nightstrike2009 on 2010-03-10
Thanks keeper that got me my options back **compiz-fusion-plugins-extra** was missing

Reflection & Deformation is locked to cylinder mode if you change it it just ignores you even if set to none or sphere, weird :-(

---

### Post by donkihote on 2010-03-19
Guys, i just wanna refresh this topic, there are no 3d windows so far?

---

### Post by meborc on 2010-03-19
> **donkihote said:**
> Guys, i just wanna refresh this topic, there are no 3d windows so far?

you get 3d windows when you install the compiz-fusion-plugins-extra package like stated earlier ;)

---

### Post by switch10 on 2010-03-19
> **meborc said:**
> you get 3d windows when you install the compiz-fusion-plugins-extra package like stated earlier ;)

yes you need to install compiz-fusion-plugins-extra

---

