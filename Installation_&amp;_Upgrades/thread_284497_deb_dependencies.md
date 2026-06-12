---
title: "deb dependencies?"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by malfist on 2006-10-25
I was trying to install a deb package not available in the repositories and when I used sudo dpkg -i *packagename* it listed dependencies, is there a command to automaticaly get those?

---

### Post by az on 2006-10-25
sudo apt-get -f install

---

