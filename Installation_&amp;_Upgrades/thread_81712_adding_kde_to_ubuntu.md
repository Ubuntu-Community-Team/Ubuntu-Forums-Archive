---
title: "adding kde to ubuntu?"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by oldmanstan on 2005-10-25
ok, couldn't figure out where this should go so it's gonna go in this forum...

is it possible to run both gnome AND kde on one system and switch between them? (pretty sure this is a "yes" but just to check) and then if I was to do this would i just need to install the necessary kde packages from synaptic?  or is it more complicated than that?

---

### Post by landotter on 2005-10-25
yes.

You can have a multitude of environments installed and choose at login. Personally I have Gnome, XFCE4, and Blackbox.

to add KDE simply install kubuntu-desktop in Synaptic. It is a meta-package and will install most but perhaps not all KDE packages you may find useful.

---

### Post by WolfJay_83 on 2005-10-25
To install KDE and XFCE, in terminal:

```

sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop

```

---

