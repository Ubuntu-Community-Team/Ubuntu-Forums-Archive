---
title: "It is possible? (changing distribution)"
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by ayozito on 2012-07-05
Hi!

Right now I have a Lubuntu running on my old laptop. I don't like it, but I have many things installed, configured, etc.. so I don't want to uninstall it.

I'm wondering if I can install for example a Ubuntu keeping the same software and configurations, and getting rid of Lubuntu programs.

---

### Post by lukeiamyourfather on 2012-07-05
You can just install Ubuntu packages if you want. Removing every trace of Lubuntu from an existing install would be impractical.

```
sudo apt-get install ubuntu-desktop
```

When the login screen is presented you can choose between the different desktop interfaces (like LXDE, Unity, etc.). If you want to literally have only Ubuntu for whatever reason like insufficient disk space I'd reinstall.

---

### Post by black veils on 2012-07-06
you could hide the lxde menu items though, by editing their files. 

after you have the desktop environment you want, open the Terminal, enter ```
gksudo nautilus
``` or whichever file manager you will be using, this will give you privileges to edit those files.

then go to ```
/usr/share/applications
``` dont delete anything, just right-click and open files with a text editor. add the line ```
NoDisplay=true
``` to the end of each file you want to hide from the menu, and save.

---

