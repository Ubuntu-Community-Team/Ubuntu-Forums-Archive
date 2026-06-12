---
title: "Synaptic Package Manager"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Foxfire on 2008-08-26
If I install Kubuntu KDE 4 desktop system  then want to delete it later will it mess up my Gnome part of Ubuntu?

---

### Post by firefeather on 2008-08-27
You might want to change the thread title to something more descriptive, like "Installing Kubuntu KDE 4 over Gnome: uninstall problems?" since this problem is not with Synaptic Package Manager.

I do believe it may be hard to clean up and make sure everything is gone, but if you are worried about having uninstalled something you needed from the Gnome desktop, you can always go to Synaptic and have it re-install the ubuntu-desktop package.

Another alternative to installing the KDE4 system if you want to try it out is to try the LiveCD---lots less to worry about if you don't like it.

---

### Post by aysiu on 2008-08-27
If you're worried about it, don't use Synaptic.

Use *apt-get* instead: ```
sudo apt-get update
sudo apt-get install kubuntu-kde4-desktop
``` Highlight all the new packages to be installed and then paste them into a text file. If you want to remove KDE 4 later, do ```
sudo apt-get remove
``` and then paste back those previously installed packages.

---

