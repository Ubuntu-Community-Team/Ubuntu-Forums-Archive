---
title: "Removing wine apps from menu bar"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by StarLog on 2007-05-06
How do I remove the apps that I loaded that do not work like Skype, and Free World Dialup, from the Applications->Wine-> drop down menu.?

Thanks

---

### Post by starcraft.man on 2007-05-06
Easy, System > Preferences Main Menu (I believe its menu layout in older than feisty).

Then navigate to the entry in the menu and uncheck the box next to it.

Some things are just simple, have fun :)

---

### Post by david_kt on 2007-05-07
> **StarLog said:**
> How do I remove the apps that I loaded that do not work like Skype, and Free World Dialup, from the Applications->Wine-> drop down menu.?

Thanks

Open .config in your home folder, and deleted/edit it there.

DK

---

### Post by YokoZar on 2007-05-07
If they don't work you can always just uninstall them: open a terminal and type "wine uninstaller"

---

### Post by StarLog on 2007-05-07
Excellent, both ways will be tried. Thanks

---

### Post by david_kt on 2007-05-08
> **YokoZar said:**
> If they don't work you can always just uninstall them: open a terminal and type "wine uninstaller"

This is the problem. Wine uninstaller do not remove the menu. Seaching in file system (usr/share/applications) is also useless. Luckily finally I found it in user/.config folder, and able to delete it manually.

DK

---

