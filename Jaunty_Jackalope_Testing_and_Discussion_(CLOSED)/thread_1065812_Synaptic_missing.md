---
title: "Synaptic missing"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by peterthewolf on 2009-02-10
I have installed 386 Jaunty on a spare asus pundit. Install went OK but under system admin I do not have "synaptic package manager". What is wrong:confused:

---

### Post by Nullack on 2009-02-10
Current repo wants to uninstall a bunch of items...Since youve done it, wait untilo the repo gets sorted and do an ubuntu-desktop install.

---

### Post by peterthewolf on 2009-02-10
Tried that but update-desktop install gives unknown command

---

### Post by Nullack on 2009-02-10
Once Colins new [ubuntu/jaunty] ubuntu-meta 1.133 (Accepted) comes down into the repos:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop

---

