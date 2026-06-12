---
title: "How to get the the &quot;desktop&quot; on ubuntu server edition"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by Agate on 2007-07-24
I have ubuntu server edition installed but i am unable to figure out how to get the the GUI.  IS there even a GUI on the server edition?

---

### Post by kevinlyfellow on 2007-07-24
The server edition uses the repos right?

Depending on the desktop you want, you can just do something like this
```
sudo apt-get install ubuntu-desktop
```

But I'd imagine you would want something lightweight for a server, in which case, you just need to install the window maker you want and xorg.

---

### Post by tgm4883 on 2007-07-24
sudo apt-get ubuntu-desktop

That will install the default ubuntu install

---

### Post by CrucifiedEgo on 2007-07-24
In a server environment, you'll definetly want to replace ubuntu-desktop with xubuntu-desktop.  xfce will be much lighter RAM-wise than GNOME, and have mostly the same functionality.

---

