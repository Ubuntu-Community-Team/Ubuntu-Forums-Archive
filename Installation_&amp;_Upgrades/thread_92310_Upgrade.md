---
title: "Upgrade"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by juancruz on 2005-11-19
Hi, I was just gifted by a friend with an original Ubuntu 5.04 version.
Im new at Linux and I just realized that there is a new version, 5.10 ?, my question is: if i want to upgrade, whatdo I have to do?
Greetings from South America, I live at Buenos Aires.

---

### Post by taurus on 2005-11-19
Edit your /etc/apt/sources.list and replace "hoary" with "breezy" and you also may want to comment out the lines with "backports" in then.  Then update and upgrade away...

sudo gedit /etc/apt/sources.list
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by az on 2005-11-19
If you do not have high-speed internet, you can upgrade from cd, too.  Is this the case?

---

### Post by yesplease on 2005-11-19
There is some extra information in the first post on this page: [http://www.ubuntuforums.org/showthread.php?t=74990](http://www.ubuntuforums.org/showthread.php?t=74990)

---

