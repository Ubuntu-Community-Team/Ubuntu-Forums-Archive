---
title: "gnome messed up after upgrading 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by yumrukcu on 2011-04-30
hi everyone.

i upgraded my ubuntu to 11.04 and i didnt like unity.
and installed gnome3 from ppa. then i couldnt login.
tried to remove gnome3 and everything messed up here.

when i tried apt-get install ubuntu-desktop, it gave unmet dependencies error.

i tried bunch of stuff,none solved the problem.

for now i installed xfce, and using it.

please help me to get gnome again.

---

### Post by MAFoElffen on 2011-04-30
> **yumrukcu said:**
> hi everyone.

i upgraded my ubuntu to 11.04 and i didnt like unity.
and installed gnome3 from ppa. then i couldnt login.
tried to remove gnome3 and everything messed up here.

when i tried apt-get install ubuntu-desktop, it gave unmet dependencies error.

i tried bunch of stuff,none solved the problem.

for now i installed xfce, and using it.

please help me to get gnome again.
So it sound like you were installing and removing from the command line... Remove Unity(?) Installed and removed Gnome 3(?) and now cannot install ubuntu-desktop(?)

When you removed, did you use the "--purge " tag?  My experience is some times if not, the package is still resident (even though not active) and may conflict with other packages.  Try using that tag to again 
```

sudo apt-get remove --purge package-name

```
To remove the package you want to remove and try installing the ubuntu-desktop package again...

---

### Post by yumrukcu on 2011-04-30
sorry for misleading

to uninstall gnome3, in console i did 

sudo apt-get remove libgtk-3-common

and then i couldnt login again, stucked at gdm window.

afterwards, i did bunch of things which i dont remember the order

apt-get install -f
apt-get install ubuntu-desktop
dkpg --configure -a

---

### Post by MAFoElffen on 2011-04-30
> **yumrukcu said:**
> sorry for misleading

to uninstall gnome3, in console i did 

sudo apt-get remove libgtk-3-common

and then i couldnt login again, stucked at gdm window.

afterwards, i did bunch of things which i dont remember the order

apt-get install -f
apt-get install ubuntu-desktop
dkpg --configure -a
First, I haven't personally done this or had this problem- 

But, from what I see on the libgtk-3-common install/remove package notes is that it deals with just adding and removing 2 other packages, libgtk-3-bin and libgtk-3-0...It doesn't say It removes anything, but it would have to disable or remove package libgtk2.0-cil for it to bring up the new version of gnome. 

I'm assuming that when you removed the libgtk-3-common package that it doesn't know to re-enable or reinstall the libgtk2.0-cil package...  Try reinstalling libgtk2.0-cli, then the ubuntu-desktop.

There was some notes on rolling back from gnome 3 to gnome 2 on the dev threads... If that doesn't work, I'll look through them for you.

---

### Post by yumrukcu on 2011-04-30
i solved my problem, i go over dependencies and installed gnome. thanks a lot.

---

