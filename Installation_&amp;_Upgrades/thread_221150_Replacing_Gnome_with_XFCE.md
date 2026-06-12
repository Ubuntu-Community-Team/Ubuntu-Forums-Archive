---
title: "Replacing Gnome with XFCE"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by weasel fierce on 2006-07-22
Managed to get life into our old laptop, but I want to replace gnome with xfce completely. I installed xfce, but is there a way to completely remove gnome, so I dont get gnome app's showing up and whatnot ?

Also, how would that affect the gdm login screen ? I presume there's an equivalent thing for XFCE. 

Same question for package management. I love synaptic but would that work fine or is there an alternative ?

---

### Post by taurus on 2006-07-22
You can use synaptic to remove Gnome but chances are you will miss something.  So, if you don't have any personal files or can back them up, I recommand you reinstall it with the xubuntu version.  Clean and nice...  

[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by mlind on 2006-07-22
You could use debfoster to remove/purge main gnome packages, then use deborphan to remove/purge orphaned gnome packages. Then install only synaptic and it's dependencies using aptitude.

---

