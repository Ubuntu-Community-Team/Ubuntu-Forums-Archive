---
title: "snap and apt updates"
date: 2019-07-28
forum: Installation &amp; Upgrades
---

### Post by apg6xswhjc on 2019-07-28
Hi

Kinda new to the whole snap thing, so hoping I can explain this properly. 


1. I'm running 19.04 and gnome is installed via snap apparently (gnome 3.28 runtime?) and it is up to date. 

2. When I run the Software Updater app, it says "The software on this computer is up to date".

3. But when I do a sudo apt list --upgradable, it reports

```
gnome-shell-common/disco-updates,disco-updates 3.32.1-1ubuntu1~19.04.1 all [upgradable from: 3.32.0+git20190410-1ubuntu1]
gnome-shell/disco-updates 3.32.1-1ubuntu1~19.04.1 amd64 [upgradable from: 3.32.0+git20190410-1ubuntu1]

```
I'm confused :confused:

Should I upgrade these manually from the command line?
Shouldn't the Software updater show that these packages are upgradable?

TIA

---

### Post by deadflowr on 2019-07-28
[Phased-Updates]("https://wiki.ubuntu.com/PhasedUpdates")

(Software Updater = update manager, ftr)

---

### Post by apg6xswhjc on 2019-07-29
Fantastic! Thanks for the information.

I could see those packages listed on the [phased update list]("https://people.canonical.com/~ubuntu-archive/phased-updates.html")

---

