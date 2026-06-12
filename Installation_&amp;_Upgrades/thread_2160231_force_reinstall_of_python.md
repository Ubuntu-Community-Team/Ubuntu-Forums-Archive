---
title: "force reinstall of python"
date: 2013-07-06
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2013-07-06
Hi
python is messed up so I need to reintall that crap.
The problem is that it wants to remove desktop and 10000 other things. 
how without removing stuff?
Many thanks

---

### Post by Cheesehead on 2013-07-06
I suppose the easy way is to use the package manager's --reinstall flag...if a corrupted file is really the problem.

Sometimes, "messed up" can mean a different problem, that reinstalling does not help.

---

### Post by MikeCyber on 2013-07-06
reinstall would probably do but the f* Ubuntu won't let me regardless of what I try.

---

### Post by dino99 on 2013-07-06
something to check before blaming a package:
-warnings/errors inside logs
- /var/crash/
- possible conflict(s) with non genuine stock ubuntu (ppa)

so use ppa-purge if necessary
and update, then check : sudo apt-get -f install
also use : sudo dpkg-reconfigure packagename

and/or : sudo dpkg-reconfigure -phigh -a
(be patient, can take a while before it end itself)

---

### Post by MikeCyber on 2013-07-07
I didn't use a ppa. I've compiled pyhton 2.6.2:

[http://www.blenderartists.org/forum/showthread.php?299474-Blender-2-49b-python-2-6-2-Ubuntu-13-04](http://www.blenderartists.org/forum/showthread.php?299474-Blender-2-49b-python-2-6-2-Ubuntu-13-04)

now that broke the whole os, like updatemanager etc. are not working anymore.
HENCE I NEED TO REINSTALL DEFAULT Python, but Ubuntu seems to never have thought that far!

---

