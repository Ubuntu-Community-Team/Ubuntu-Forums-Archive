---
title: "Want to reinstall Ubuntu but I dont want to download all the softwares again so can I"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by iampriteshdesai on 2008-06-16
I have installed Ubuntu using Wubi, now I am going to reinstall windows and hence I will have to reinstall Ubuntu. I have downloaded Vlc and Dvd support along with other softwares for Ubuntu I dont want to download them again. I know that the software packages are stored locally so using them can I install them next time?

---

### Post by meindian523 on 2008-06-16
I believe you can install APTonCD and backup your packages to CD,then install on your HDD installed system.Please search in Synaptic.

EDIT:Also,so that you don't have to reinstall Ubuntu,every time you reinstall Windows,you can create a dual boot,that is install Ubuntu on the HDD along Windows.

---

### Post by bigken on 2008-06-16
yep aptoncd is the way to go

---

### Post by iampriteshdesai on 2008-06-16
I have saved the files downloaded to var/cache/apt/archives
can i use it to install vlc, wine and libdvd next time?

---

### Post by meindian523 on 2008-06-16
you can but it's preferable to use APTonCD.

---

### Post by -random on 2008-06-17
aptoncd in the terminal gives me:

```
2512
Note: there are some packages installed that are not available in cache
```

So.. how can I do a refresh or something so that all packages are in /var/cache/apt/archives ?:confused: 

( I know for example for a single package you can just re-install it and it'll show up on aptoncd, but wont this bump something else out of the cache? does the cache have a max size or something? where are the packages that aren't in cache? )

---

### Post by meindian523 on 2008-06-17
cache doesn't have a max size.packages which are not in cache have not been installed using Synaptic,so they will be wherever you downloaded them to.APTonCD has a GUI,why are you trying the CLI?

---

### Post by -random on 2008-06-17
i'm using the gui, just launced it with a terminal. ( don't know where else 2 find it)

Also, my apt-get doesn't work in CLI and i'm waaaay too lazy 2 download a .deb file. Somehow vlc didn't show untill i re-installed it (in synaptic again), but i'm gonna try 2 use aptoncd and hope that everything is there..

---

### Post by meindian523 on 2008-06-17
APTonCD is in System>>Administration.What do you mean apt-get doesn't work in CLI?Does it give any errors?

---

### Post by -random on 2008-06-17
ye i found it there right after the post lol, but thanks anyway..

yes, apt-get doesn't go through my proxy or something but i don't care cause i only use synaptic anyway, even if it takes me couple of seconds longer to add a single package ;)

---

