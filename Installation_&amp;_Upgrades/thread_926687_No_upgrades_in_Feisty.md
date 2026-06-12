---
title: "No upgrades in Feisty"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by sambarluc on 2008-09-22
Hi,
I am trying to upgrade a Kubuntu installation from 7.04 to 7.10, but I do not find any possible upgrade both with adept manager and apt-get.
I also tried to substitute "fesity" with "gutsy" in sources.list, but nothing changed.
Any idea?

---

### Post by Pumalite on 2008-09-22
You need to have your OS fully update. Remove all third parties from your sources.list. Then you might want to try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

P.S. I prefer clean installs

---

### Post by sambarluc on 2008-09-22
I already tried all of this, with no result at all!

---

### Post by sambarluc on 2008-09-22
Seems that some mess has been done. I found that the system had feisty repositories but, in fact, 7.10 is installed (I am not the only user). I changed repositories to gutsy, updated, but there is still no available upgrade in adept manager.
How can I upgrade to hardy? (that, in fact, was my final aim)

---

### Post by oilchangeguy on 2008-09-22
> **sambarluc said:**
> Seems that some mess has been done. I found that the system had feisty repositories but, in fact, 7.10 is installed (I am not the only user). I changed repositories to gutsy, updated, but there is still no available upgrade in adept manager.
How can I upgrade to hardy? (that, in fact, was my final aim)

why make life hard? just back up any data you have. burn an 8.04 cd, and do a fresh install.

---

### Post by sambarluc on 2008-09-22
That IS making life hard.

---

### Post by sambarluc on 2008-09-22
Changed the repositories to hardy, now upgrades do work.

---

