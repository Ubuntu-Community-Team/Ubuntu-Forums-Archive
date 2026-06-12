---
title: "Chrome removed after upgrade to 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by amirfoad on 2011-10-17
Hi.
I've installed Google Chrome in Ubuntu 11.04 by downloading the installation package directly from google.com but it removed automatically after upgrading to 11.10 and I couldn't reinstall it from .deb package.
Is there any way to use it in 11.10?

---

### Post by amirfoad on 2011-10-17
Any suggestions yet?

---

### Post by prettyboy85712 on 2011-10-17
sudo apt-get -f install

---

### Post by amirfoad on 2011-10-17
> **prettyboy85712 said:**
> sudo apt-get -f install
this is the result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-11 linux-headers-3.0.0-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jimbo99 on 2011-10-17
He might have meant.

sudo apt-get -f install <package.deb>

Obviously <package.deb> is the name of the package you would substitute.  I think the -f means to force the install.

---

