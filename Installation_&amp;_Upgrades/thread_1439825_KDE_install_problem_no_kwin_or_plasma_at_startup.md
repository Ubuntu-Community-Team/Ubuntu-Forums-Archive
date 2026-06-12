---
title: "KDE install problem: no kwin or plasma at startup"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by eje211 on 2010-03-26
I just made a fresh install of Ubuntu. Actually, I wanted Kubuntu, but, as I'd burned Ubuntu, I just installed it and added Kubuntu from apt-get. But now, when KDE starts, all I get is a Gnome Terminal window. No kwin, no plama. I can start everything myself, but I'd like it to be done automatically.

I think it's an Xsession thing, but I'm not sure. I don't have the full KDE startup animation, and I actually think that what I get is a "blank" X that I change into KDE by starting kwin and Plasma.

Also, the only way I can stop KDE is by closing that Gnome Terminal window. And when I'm the KDM prompt, I don't get the shutdown and restart options directly. I don't get them at all from inside KDE. Something Gnome is looming over my KDE, but what is it?

Thanks to all who can help.

---

### Post by eje211 on 2010-03-27
This was much simpler than I thought. And it took me hours. I just needed to select "KDE" in KDM. I thought it was the default desktop, but, apparently, it was not.

---

### Post by Chame_Wizard on 2010-03-27
```
sudo aptitude install kubuntu-desktop
```:popcorn:

---

