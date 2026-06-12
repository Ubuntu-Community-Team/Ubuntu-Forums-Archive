---
title: "Removing Gnome Panel"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sekinto on 2009-04-06
How do I remove the last Gnome Panel, I want to completely substitute it with Avant Window Navigator. I want a solution that stops it from even starting, I don't want a solution that just "hides" it (because then it would still take up resources).

---

### Post by phenest on 2009-04-06
```
sudo apt-get remove gnome-panel
```

If it says it wants to remove things like ubuntu-desktop, don't worry, it's only removing the meta-package and not the actual desktop.

I use AWN too, so this is what I did. If you want to prevent it from being reinstalled during upgrades, simply lock the version of gnome-panel in Synaptics.

---

### Post by sekinto on 2009-04-06
I was kind of hoping to keep it installed as a backup, but I guess I have Xfce installed also.

---

### Post by aamukahvi on 2009-04-06
I have not tried this and I don't know if it will break something but setting gnome-panel as not executable might do the trick:
```
sudo chmod -x /usr/bin/gnome-panel
```

Give it a try in a virtual machine first...

---

### Post by sekinto on 2009-04-06
I uninstalled it and am not getting any problems so far, thank you very much. :]

---

### Post by kansasnoob on 2009-04-06
> **phenest said:**
> ```
sudo apt-get remove gnome-panel
```

If it says it wants to remove things like ubuntu-desktop, don't worry, it's only removing the meta-package and not the actual desktop.

I use AWN too, so this is what I did. If you want to prevent it from being reinstalled during upgrades, simply lock the version of gnome-panel in Synaptics.

I've always believed that that will bork future updates to some degree. I could be wrong!!!!!!

But you should be able to go to System > Preferences > Main Menu and if you click on System Tolls you can "tick" Configuration Editor.

Then go to System Tools > Configuration Editior and - well a picture is worth a thousand words:

[ATTACH]108909[/ATTACH]

You can see that I expanded Desktop, then Gnome, then Session. From there you can deselect panel from "required components".

BUT if you break it you own it!

I've done a lot of playing with different desktop arrangements, especially LXDE and E-17, and I'm always prepared for full breakage which means a reinstall!

---

### Post by kansasnoob on 2009-04-06
Regarding ubuntu-desktop quoting from synaptic:

> This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

---

