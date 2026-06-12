---
title: "OpenJDK Firefox plugin"
date: 2008-07-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nerd_bloke on 2008-07-15
After a fresh install of Alpha 2 i tried to add the icedtea-gcjwebplugin. If anyone else gets the behavior below then I will log a new bug on Launchpad.

The openJDK runtime and other dependencies seemed to install OK but the plugin returns that 
/etc/alternatives/firefox-javaplugin.so
hasn't been created so it doesn't make its symlink and therefore fails to complete.

---

