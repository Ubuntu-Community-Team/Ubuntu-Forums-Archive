---
title: "aptitude strange behaviour"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by restart on 2010-03-28
Hi all.

About a month ago I tried install new KDE 4.4 from the thrid party ppa. I didn't like it so I removed everything that I installed.
But!

If I type
```
aptitude install -f
```
I recieve the messages about the KDE components missing their dependencies. The output looks like this:
```
$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  alien-arena amarok-utils cdrdao dragonplayer exiv2 exo-utils k3b 
kamera kcm-gtk kde-style-qtcurve kde-zeroconf kdebase-bin 
kdebase-workspace kdebase-workspace-kgreet-plugins
........ <much more packages here> .........

```
after this aptitude offers a solution to fix the dependency problems (install full KDE desktop).

But this packages are ALREADY removed from the system, so why are they broken? Each package in this list are not present in the system so 'aptitude[apt-get] remove <package_from_BROKEN_list>' doesn't work.

By the way:
```
apt-get install -f
```
says that everything OK.

---

### Post by mac9416 on 2010-03-28
I'm shooting in the dark, but I'll offer a suggestion. Try disabling the KDE PPA and running 'sudo aptitude update'. Maybe this will make something click in Aptitude.

---

