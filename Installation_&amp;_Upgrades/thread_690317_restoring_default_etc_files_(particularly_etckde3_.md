---
title: "restoring default etc files (particularly /etc/kde3 and kdmrc)"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by timtoo on 2008-02-07
Files in my /etc/kde3/kdm got corrupted (don't ask) and so I wiped them the /etc/kde3/kdm directory. I figured i could just reinstall the kdm package with apt-get and the default config files would be restored. Now, this doesn't seem to be the case.

I went so far as to completely "apt-get remove" all of kde/kubuntu-desktop (and all the packages it installs), deleted /etc/kde3 and did an "apt-get install kubuntu-desktop" ... but  i find my /etc/kde3 directory still virtually empty, and kdm presents a default view (ie. no theme, all users available for selection, and login always starts a single xterm window with no window manager). 

I've tried using dpkg-reconfigure ("dpkg-reconfigure -a" even) but still no kubuntu default config files appear. I did notice at one point a bunch of config file dis appear with "-new" appended to the filename, but when the process finished those files were gone and the config directories empty. It's as if the system knows I deleted them and thinks i want them deleted, so refuses to put the "new" ones in place. 

Can someone who knows the details of the apt system give me some clues as to how/why I can't get these default files in /etc to be installed again? Maybe just a switch i'm missing somewhere?

---

