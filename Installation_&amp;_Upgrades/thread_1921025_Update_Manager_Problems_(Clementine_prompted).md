---
title: "Update Manager Problems (Clementine prompted)"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by hybridxdawn on 2012-02-05
Hey all, I've tried to update the Clementine to the new 1.0 version, running 11.10, and now I get this error when I try to update my software:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/me-davidsansome-clementine-oneiric.list'

I'm kind of a linux newbie, what should I do here?

---

### Post by hybridxdawn on 2012-02-05
Here's the full error message:

> An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/me-davidsansome-clementine-oneiric.list'

---

### Post by oldos2er on 2012-02-05
That file should look like 
```
deb [http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu) oneiric main  
deb-src [http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu) oneiric main
```You can edit it with the command ```
gksu gedit /etc/apt/sources.list.d/me-davidsansome-clementine-oneiric.list
```

---

### Post by hybridxdawn on 2012-02-05
thank you! fixed. will mark the thread!

---

