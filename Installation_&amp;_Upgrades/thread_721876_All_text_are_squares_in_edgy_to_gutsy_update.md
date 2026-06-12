---
title: "All text are squares in edgy to gutsy update"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by alpha_Jack on 2008-03-11
Hi guys, I was updating from 6.10 edgy to gutsy when something went wrong, now all the text in my screen are squares instead, there is no font, luckily this only affects gnome apps, so the web browser is still useable, I've looked at similar problems on the forum and none of them seem to be answered.


I'm not sure if this is connected, but in console, when I try to use 

sudo apt-get dist-upgrade

is goes as such

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
  udev: Breaks: libdevmapper1.02 (< 2:1.02.08-1ubuntu7) but 2:1.02.07-1ubuntu2 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.


any help would be sorely appreciated

---

### Post by bumanie on 2008-03-11
It is advisable to upgrade only to the next distro above your present one. I don't know if it too late now or not with what you have already done, but you should upgrade to 7.04, before trying to update to 7.10.

---

### Post by alpha_Jack on 2008-03-11
....is it too late?

---

### Post by zvacet on 2008-03-12
Did you download Gutsy updates?Or your upgrade just failed?If it is failed make your source list like it was (edgy source list) and do 

```
sudo apt-get update && sudo apt-get upgrade
```
 
which should make your system up-to-date.If that pass O.K. go to the update manager and upgrade to Feisty.Then to Gutsy.If that is not possible do the fresh install of Gutsy.

---

