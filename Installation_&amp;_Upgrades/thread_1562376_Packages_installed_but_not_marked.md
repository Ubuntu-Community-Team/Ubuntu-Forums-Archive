---
title: "Packages installed but not marked"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by gavdari on 2010-08-27
Recently I have a problem with Software Center and Synaptic. When I use either one to install a package, it downloads and installs just fine, but I can't use it. When I recheck it  in Synaptic, there is no mark beside it (like it's not installed) but available options are Reinstall, Remove or Complete Removal (see attachment). I have checked the problem with Clamav and Samba and their dependencies, both are the same.

---

### Post by quixote on 2010-08-29
There's no "Broken" heading in the left pane in synaptic unless there are broken packages.  They may be what's causing the problems.  Under Edit in the menu, there's a choice to "Fix Broken Packages."  Try that, and let's see if it helps.  Alternatively, there's the command line ```
dpkg --configure -a
```which is often more thorough and robust.

---

