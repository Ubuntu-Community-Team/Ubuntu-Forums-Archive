---
title: "dpkg vs apt-get"
date: 2005-10-06
forum: Installation &amp; Upgrades
---

### Post by asterix404 on 2005-10-06
when installing which one should I use? Are they both interchangable being package managers who I am guessing goto the same servers for thier package needs?

---

### Post by Zelut on 2005-10-06
apt-get will retrieve and install the package, dpkg is the command to install it yourself.  I believe apt-get may even use dpkg once its finished retrieving the files.

for example: 
apt-get update will check for updates with the repository
apt-get upgrade will upgrade the differences using dpkg

if you've manually downloaded a .deb file you should use dpkg but as far as I know it wont retrieve any files for you

---

### Post by aysiu on 2005-10-06
apt-get will resolve dependencies. dpkg won't.

---

