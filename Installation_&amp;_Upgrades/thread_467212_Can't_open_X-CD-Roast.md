---
title: "Can't open X-CD-Roast"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by swoll1980 on 2007-06-07
Tried "gksudo X-CD Roast" told me command did not exist it's In my application menu when I click it it tells me it has no root file to open it from a terminal. Can someone help me with this?Please.

---

### Post by empthollow on 2007-06-07
i believe the command would be 
```
gksu xcdroast
```
commands are one word where as menu items are viewed as anything you want to call the item, for example "text editor" in the menu actually runs the command "gedit". if you want to find out exactly what the menu is running right click on the menu and click edit, find the item and right click, then choose properties.  the "command" field will contain the command line version.

---

