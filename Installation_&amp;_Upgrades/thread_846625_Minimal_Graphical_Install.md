---
title: "Minimal Graphical Install"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by dethredic on 2008-07-01
Ok, I am setting up server and I have it about half set up. Is there a way to install the desktop environment without all the extras?

All I need is:
a) Firefox
b) Pidgin
c) Gedit
d) Gimp
e) PDF viewer
f) flash / java

I don't need all those extra games and programs that come with it. What is the easiest way to do this? Also would Xubuntu be better?

Finally, I have gone through my /etc/atp/sources.list and removed all the #'s in front of the url's so I get all the sources which means more packages or however it works. 
When I try apt-get install ubuntu-desktop I get: "E: couldn't find package ubuntu-desktop".
I would gladly post my sources.list, but I have no idea how to copy it over here.

---

### Post by SkonesMickLoud on 2008-07-01
Xubuntu would be the best for you.

Paste:
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Into a terminal.

You can install/uninstall any packages you want/don't want afterwards.

You could also try a minimal install with IceWM, FluxBox, or something like that:

[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

---

### Post by Pumalite on 2008-07-01
Wrong post.

---

### Post by dethredic on 2008-07-01
> **SkonesMickLoud said:**
> Xubuntu wold be the best for you.

Paste:
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

Into a terminal.

You can install/uninstall any packages you want/don't want afterwards.

You could also try a minimal install with IceWM, FluxBox, or something like that:

[http://psychocats.net/ubuntu/minimal#barebones](http://psychocats.net/ubuntu/minimal#barebones)

I am going with Xubuntu I guess. Your code is working. What is the difference between aptitude and apt-get and when should I use each?

---

### Post by SkonesMickLoud on 2008-07-01
> **dethredic said:**
> What is the difference between aptitude and apt-get and when should I use each?

Aptitude is a front end to apt-get.  If you were to run "aptitude" as a command, you'd get a package manager along the lines (albeit not as pretty as) Synaptic, which allows you to select packages much the same.

As far as I know apt-get and aptitude can be used interchangeably.

Just remember that anytime you change sources.lst, it is a good idea to run "sudo apt-get/aptitude update".

---

### Post by dethredic on 2008-07-01
> **SkonesMickLoud said:**
> Aptitude is a front end to apt-get.  If you were to run "aptitude" in a command, you'd get a package manager along the lines (albeit not as pretty as) Synaptic, which allows you to select packages much the same.

As far as I know apt-get and aptitude can be used interchangeably.

Just remember that anytime you change sources.lst, it is a good idea to run "sudo apt-get/aptitude update".

Ok, well I updated like 20 times, that is why I am confused.

---

### Post by dethredic on 2008-07-06
Ok, now that the server is set up I do not really need the xubuntu desktop, but I would like to keep it as a backup. Currently it boots straight into the desktop. Is there any way to make it boot into the command line to start and then I can type in startx if I need to start the desktop environment?

---

### Post by dethredic on 2008-07-07
anyone?

---

