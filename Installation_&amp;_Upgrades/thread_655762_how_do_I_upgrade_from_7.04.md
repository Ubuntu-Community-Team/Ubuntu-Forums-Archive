---
title: "how do I upgrade from 7.04?"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by bobbybiceps on 2008-01-01
when I go to update manager and update everything, I do not get message stating that an upgrade to 7.10 is available - how do I start the upgrade?

---

### Post by Pumalite on 2008-01-01
Take a look at this:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
You might want to try this too:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

