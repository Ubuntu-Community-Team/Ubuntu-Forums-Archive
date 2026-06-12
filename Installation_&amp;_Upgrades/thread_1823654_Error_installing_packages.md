---
title: "Error installing packages"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by iDrago on 2011-08-12
Hi,
I've a little problem.
When I want install a package, I get this error (an example with thunderbird) : 

[http://pastebin.com/BLL90v6Y](http://pastebin.com/BLL90v6Y)

But the package is installed anyway.
 Do you have an idea?
 Apparently this would be due to some themes whose path doesn't exist.

Thx, iDrago ;)

---

### Post by dino99 on 2011-08-12
dpkg: erreur de traitement de plymouth-theme-mib-oxygen
dpkg: erreur de traitement de plymouth-theme-spinfinity-ubuntu-women

something borked with these themes, will remove them:

sudo apt-get purge plymouth-theme-mib-oxygen
sudo apt-get purge plymouth-theme-spinfinity-ubuntu-women

---

### Post by iDrago on 2011-08-13
Thx, it's fixed.

---

