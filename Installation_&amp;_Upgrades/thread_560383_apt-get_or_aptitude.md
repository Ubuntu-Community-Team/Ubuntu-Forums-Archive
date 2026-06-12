---
title: "apt-get or aptitude"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-26
From Feisty and for the future is there any difference if I use apt-get or aptitude for installation and/or removal.  I understand that there was a dependency issue with previous versions.

---

### Post by LaRoza on 2007-09-26
People say no, but I only use aptitude, for no particular reason.

---

### Post by Pumalite on 2007-09-26
Aptitude is better for easier, total and complete removal of a package later.

---

### Post by borris.morris on 2007-09-26
aptitude typically removes and installs things more completely.

---

### Post by dptxp on 2007-09-26
some say that apt-get is as good as aptitude now. Synaptics and Add/Remove most probably
use apt-get. I have stuck to aptitude.

---

### Post by dabl on 2007-09-26
Same-same.

Here's more: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

:)

---

### Post by stchman on 2007-09-26
> **measekite said:**
> From Feisty and for the future is there any difference if I use apt-get or aptitude for installation and/or removal.  I understand that there was a dependency issue with previous versions.

Use apt-get.  I have found that when I use aptitude to remove programs it wants to uninstall programs that I still want.  Since the advent of Edgy aptitude is no longer needed.  

To install a program with apt-get do the following (Ex.):

```
sudo apt-get install k3b
```

This will install K3B and all the required dependencies.  To remove K3B and all its dependencies do the following:

```
sudo apt-get autoremove k3b
```

So remember to use autoremove instead of remove as remove only removes the program and not the dependencies.

---

