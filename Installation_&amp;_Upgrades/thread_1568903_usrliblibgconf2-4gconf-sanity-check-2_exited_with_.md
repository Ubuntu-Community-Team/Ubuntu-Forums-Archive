---
title: "/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by techmaniack9 on 2010-09-06
yesterday i tried to install bt4 from alongside ubuntu 10.04. Unfortunately the DVD had some errors and the installation stopped. Everything was fine till then, even the GRUB was working(i guess!) but when i tried to log into my Ubuntu it gave me an error...

[INDENT]" 				**/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with error status 256**"
[/INDENT]
also there was a popup like "gnome power management was not properly installed ....blah blah blah Contact you network admin"


i have only one user on that system. 
i tried the single user mode but no success...
i then tried to Ctrl+Alt+F1-F6 no success... can't switch to command line(this is my display problem i guess)
 

i have now decided to install a fresh install but i do need to take the backup. What all should i copy to the new install so that i get the same feel as before???!!!???

---

### Post by davedavee on 2010-12-09
maybe have a problem with permissions....
try
```
sudo chmod 755 /etc/gconf/gconf.xml.*
```
i had same problem and this helped...

---

