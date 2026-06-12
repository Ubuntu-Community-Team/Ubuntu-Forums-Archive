---
title: "restoring ex-backups in new system"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by sinaphysics on 2012-04-09
Hello,
I have backups of my ex-ubuntu 11.10. after installing new ubuntu(same version) on my system I want to restore my backups which was from( /var/cache/apt/archives ). I restore it to same address and then type ```
sudo apt-get update
sudo apt-get install "package"
``` when I'm offline.
but my softwares couldn't be restored. what do u suggest??
Is there other way because it's near 2 months I can't find anyway!! :(
please pay attention that I haven't high speed internet to download all packages again!

---

### Post by zvacet on 2012-04-11
If you still have folder with your packages then removev them from /var/cache/apt/archives and from terminal go to the folder where packages are and type

```
sudo dpkg -i *deb
```

That will install all packages.

---

