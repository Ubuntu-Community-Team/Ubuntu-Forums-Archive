---
title: "Suggestion for gutsy update manager"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by timforlinux on 2008-03-03
The update manager should remember when you ** uncheck** something.  Mine keeps trying to update audacity (in gutsy).  However, audacity 1.3 does not work so I want to keep 1.2.   Unless I remember to uncheck it everytime ubuntu self updates, or if someone else runs the updates,  I get 1.3 back again.  The Updater should keep a list (tab) of 'available but not wanted right now.'

  Similarly, the Updater recently suggested I spend several hours getting rid of old stuff and doing a major update.  I couldn't do that at the time.  But the option has never reappeared.  That too should be available somewhere to select when convienient.

tim

---

### Post by plucky on 2008-03-03
timforlinux,


Why don't you just lock the version of package you want,so the updater doesn't try to upgrade it.
Use **Synaptic Package Manager** ,select the package you want to keep by left clicking on it,select package tab and click on **lock version**.

> 
Similarly, the Updater recently suggested I spend several hours getting rid of old stuff and doing a major update. I couldn't do that at the time. But the option has never reappeared. That too should be available somewhere to select when convienient.

Open a terminal and ```
sudo apt-get update 
sudo apt-get upgrade
``` should do it for you.


Good luck

---

### Post by kwacka on 2008-03-08
```
sudo apt-get hold audacity
```
in a terminal will stop it getting updated.

```
sudo aptitude unhold audacity
```
removes the restriction.

---

