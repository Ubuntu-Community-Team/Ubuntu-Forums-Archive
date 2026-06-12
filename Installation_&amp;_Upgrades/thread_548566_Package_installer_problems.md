---
title: "Package installer problems"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by hhhonchor on 2007-09-11
Hi, I recently tried to install virtualbox, but the installation failed and now any attempt to use synaptic or to install a package gives the following message:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

Any suggestions?

---

### Post by wolfen69 on 2007-09-11
it sounds like your sources list is borked. go here [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to generate a new one. then:
```
gksudo nautilus
```
navigate to /etc/apt/sources.list and replace sources.list with the new one. then:
```
sudo apt-get update
```

---

### Post by hhhonchor on 2007-09-11
Okay chief thanks I'll give that a shot.

---

### Post by dabl on 2007-09-11
Also wouldn't hurt to ```
sudo dpkg --configure -a
``` to make sure the package manager is in good shape. :)

---

