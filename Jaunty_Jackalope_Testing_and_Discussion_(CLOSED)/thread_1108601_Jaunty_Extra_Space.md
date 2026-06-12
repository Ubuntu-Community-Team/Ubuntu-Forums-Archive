---
title: "Jaunty Extra Space?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by shark1997 on 2009-03-27
I was wondering whether to upgrade to jaunty or do a clean install. Does upgrading take more space? I only have 9gb on my / partition and that is my only partition.

---

### Post by daveg2 on 2009-03-27
I needed slightly over a GB of free space when I upgraded.  I believe it was apt-get clean to remove the install files when done.

---

### Post by tommcd on 2009-03-28
Using apt-get clean will remove all of your local repository of downloaded packages. This is harmless. If you ever need to reinstall something, you can just download it again via apt-get or synaptic.
If you would like to keep the repository of packages you have installed, run apt-get autoclean. This will only remove packages that are old and can't be downloaded anymore. 
Then there is apt-get autoremove, which will look for packages that were installed as dependencies for packages that have been uninstalled and removes them. So **clean** will free up the most space, and **autoclean** will free up less space but still maintain your local cache of installed packages.

---

