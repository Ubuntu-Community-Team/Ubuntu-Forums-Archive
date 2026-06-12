---
title: "Cant upgrade to 14.04:no new release found"
date: 2014-05-14
forum: Installation &amp; Upgrades
---

### Post by abhisranjan on 2014-05-14
Hi,
I use ubuntu 13.10 but I cant upgrade to ubuntu 14.04 as when I run
sudo do-release-upgrade
it returns
no new releases found.
I already have updated and uninstalled and reinstalled upgrade manager core but to no avail.

---

### Post by slickymaster on 2014-05-14
Hi abhisranjan, can you please try this in a terminal window (please issue one command at a time):```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```After that do this (again, issue one command at a time):```

sudo apt-get clean
sudo do apt-get update
sudo apt-get dist-upgrade  
sudo do-release-upgrade
```

Edit: Please, also remove all thrid party PPAs.

---

