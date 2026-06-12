---
title: "Uninstall Kubuntu?"
date: 2005-05-24
forum: Installation &amp; Upgrades
---

### Post by ceti on 2005-05-24
I intend to install Kubuntu in a new partition, but first I want to uninstall Kubuntu-Desktop from my Hoary. (I think that, in some mysteryous way, KDE is interferring with Gnome).
How do I do that? The Official Kubuntu page & the Unofficial Kubuntu Guide don't say anything on doing this.
Any help?
Thanks in advance.

---

### Post by Xian on 2005-05-24
If you want to uninstall KDE the best way is to issue the terminal command listed below. It will remove almost all of the applicable packages. What few packages remain can be removed with Synaptic by looking in the 'KDE Desktop Environment' section.
```
sudo apt-get remove kdelibs4 arts
```

---

