---
title: "Trying to transfer updates"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Gboxx on 2008-02-24
Can anybody help me please?
I have been using Gutsy 7.10 for over a couple of months now dual booting with windows XP Home on my Sony VAIO VGNFS485B and I am planning on installing it on my Dell Dimension 8200 desktop. My desktop is not directly connected to the internet and I am wondering if it is possible to transfer updates like Compiz, Wine installation, Amarok and other software that I have installed on the VAIO using synaptics to the Dell desktop without having the desktop directly connected to the internet. Any help will be good. Thanks :)

---

### Post by zvacet on 2008-02-24
All packages you installed with synaptic or apt-get are stored in var/cache/apt/archives.Install aptoncd (it is in synaptic).That program make copy of  var/cache/apt/archives and make iso.Burn iso on CD/DVD and put it in other comp.

---

### Post by Sam Lars on 2008-02-24
You could also set up apt-cache to share the package cache directly to Synaptic...

---

