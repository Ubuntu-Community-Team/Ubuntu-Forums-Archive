---
title: "uninstalling packages results in less disk space"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by hudo on 2005-05-23
Hello,

although I uninstall packages with synaptic, disc space gets less and lesser.
Where does it disappear ? 
Can someone explain me this behaviour ?

---

### Post by JonahRowley on 2005-05-23
Most packages don't take up much space.  One place to look is apt's package cache.  Is **/var/cache/apt/archives/** empty?  If not, then **sudo apt-get clean**, or there might be a way to do it through the GUI.

Check your home directory.  What does **du -hs ~** tell you?

---

