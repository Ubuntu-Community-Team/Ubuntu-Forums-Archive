---
title: "Update not working"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by Mantrasong on 2005-11-01
I just installed Ubuntu, and I attempted to run apt-get, and it returns with this error:

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)

It can't get some of the update packages, or any of the programs. Does anyone know how to fix this?

---

### Post by Kyral on 2005-11-01
Breezy-Backports and Breezy Extras are not open yet. Comment out those lines in your sources.list

---

