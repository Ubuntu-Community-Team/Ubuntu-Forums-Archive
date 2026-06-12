---
title: "aptitude is &quot;keeping back&quot; ubuntu-desktop"
date: 2009-09-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-09-27
For some reason ubuntu-desktop is being kept back by aptitude. Is this is a problem and if so, how to fix it?

```

$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages have been kept back:
  ubuntu-desktop 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

---

### Post by joey-elijah on 2009-09-27
I had the same issue - i simply went into Synaptic and upgraded from there... everything seems fine.

---

### Post by psyke83 on 2009-09-27
Run:```
$ sudo apt-get install ubuntu-desktop
```

You'll find that it wants to remove software-store and install software-center in it's place. You should read the sticky thread for more details, and get into the habit of checking changelogs.

---

### Post by doas777 on 2009-09-27
I believe that the safe-upgrade holds back any packages that don;t meet preconditions in terms of dependencies and incompatible packages. if you for instance removed a "core" desktop app, which in turn removed the ubuntu-desktop metapackage, or if you installed incompatible 3rd party software, then it probably won;t install.

---

### Post by Teamgeist on 2009-09-27
```
sudo aptitude update
sudo aptitude full-upgrade
``` will remove software-store and install software-center.

---

