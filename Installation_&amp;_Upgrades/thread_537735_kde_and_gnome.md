---
title: "kde and gnome?"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by ubuntu.daemon on 2007-08-29
so currently on my laptop i have an xubuntu installation with of course xcfe, gnome-core, and kde-core. Im doing a re-installation, is it possible to install kde, like the main one, and then have like another gnome installation that runs off the same data? Firefox, amarok etc, without being like another total installation?  I know the core packages do it without interfering, but if i install everything i think i might have issues with conflicting packages.....

---

### Post by 505 on 2007-08-29
It is possible, just install Ubuntu from a CD, then do
```
sudo aptitude install kubuntu-desktop
```
This will install Kubuntu, but leave most of the config data intact. Only things that are replaced are usplash screens, and login window, etc. From the login window you can choose your session, Gnome or KDE. You can run your KDE programs in Gnome, and Gnome programs in KDE, and the settings are shared, because there is just one /home/user folder.

---

