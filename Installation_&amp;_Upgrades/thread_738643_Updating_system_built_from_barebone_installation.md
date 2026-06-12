---
title: "Updating system built from barebone installation"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by gabng on 2008-03-28
Hi, I used Feisty to build a up a bare bone CLI system last year and manually installed the x-window-system-core and other softwares from the repository and it has been running Fluxbox nicely.

Now I'd like to upgrade it to Gutsy and later Hardy so I could get the software updates.

Since I installed everything manually from the repository, the system doesn't have the ubuntu-desktop meta packages installed, so when I do sudo apt-get dist-upgrade, it doesn't know how to upgrade.  My system is old and slow, so I don't really want to install everything associated with the meta package in order to upgrade.

My question is that if it would be possible to just replace the source.list file with gutsy repositories and then just use sudo apt-get update/upgrade?  Or would I need to reinstall everything from scratch using Gutsy CD?

Appreciate your responses.

---

### Post by gabng on 2008-03-29
Anyone?

---

### Post by Barrucadu on 2008-03-29
Have you tried this?
```
sudo apt-get install update-manager
sudo update-manager -d
```

That should launch the graphical update manager and alert you about a distribution upgrade, though I'm not too sure about feisty as I just used regular Ubuntu back then.

---

