---
title: "Upgrading from Dapper Drake - no upgrade button"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by mmmpancakes on 2008-06-17
I'm currently on Dapper Drake, hoping to update to a more current version. I've ran update manager to make sure I'm up-to-date for an upgrade. Problem is, no update button exists that allows me to upgrade to a newer version. 

Per a community Web site, I ran the following command:

> mv ~/.update-manager ~/.update-manager.old

And this is the output: 

> mv: cannot stat `/home/michael/.update-manager': No such file or directory 

Any ideas?

---

### Post by Pumalite on 2008-06-17
You might want to try this:
sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by mmmpancakes on 2008-06-17
> **Pumalite said:**
> You might want to try this:
sudo sed -i 's/dapper/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

You're my hero. Many thanks.:guitar:

---

### Post by Pumalite on 2008-06-17
You are welcome and good luck.

---

