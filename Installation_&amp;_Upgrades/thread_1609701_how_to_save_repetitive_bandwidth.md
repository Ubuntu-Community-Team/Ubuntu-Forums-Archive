---
title: "how to save repetitive bandwidth"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by gambang07 on 2010-10-30
I want to install Ubuntu on several stand alone machines without repeating the several hundreds MBs updates on each machine using Synaptic. I understand the installations/updates files would reside in var/cache/apt/archives. So I can copy them to be used for the next machine. But specifically how? And can the non-OS files in a 64-bit machine be used in 32-bit machines' updates/program installations?

---

### Post by mikewhatever on 2010-10-30
Run Nautilus with admin privileges, gksudo nautilus, or you could point it to the desired location at the same time,
```
gksudo nautilus /var/cache/apt/archives
```
and simply copy/paste.
If you prefer CLI:
```
sudo cp /var/cache/apt/archives/*deb /some-destination
```

PS:64bit programs need 64bit updates, same for 32bit.

---

### Post by gambang07 on 2010-10-30
Thanks Mike, but after copying and moving it to another machine, can you specifically tell me how to install them? Would that be highlighting the files and then right clicking them and select 'open with dpkg -debian' sth like that? Or can I use Synaptic but redirect it to find the files which I move from other machine instead of from the internet?

---

### Post by mikewhatever on 2010-10-30
Synaptic should auto-check the /var/cache/apt/archives location, just hit the reload button. You could also run the following commands:

sudo apt-get update

sudo apt-get upgrade

---

### Post by DrBubba on 2010-10-30
An alternative would be (for the cautious who haven't installed too many exotic packages): 

sudo aptitude update
sudo aptitude safe-upgrade

check to see that everything works then

sudo aptitude full-upgrade

Aptitude's safe-upgrade won't uninstall packages - even if uninstalling one may be necessary to upgrade another, so it's generally safer than apt's standard dist-upgrade.  The update manager uses something like aptitude's safe-upgrade algorithm to perform safe upgrades.

---

