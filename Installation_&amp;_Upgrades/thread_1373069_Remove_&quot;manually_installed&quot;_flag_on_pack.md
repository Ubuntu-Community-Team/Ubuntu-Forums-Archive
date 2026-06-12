---
title: "Remove &quot;manually installed&quot; flag on packages"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by Prendi on 2010-01-05
Hi,

after updating to Karmic, Synaptic shows almost all of my installed packages in the category "Installed (manual)", including about half of the packages that belong to a clean Ubuntu installation (e.g. apparmor, apt and hundreds of others). As a result, I can't easily get a list of those packages that I did indeed install manually and may want to remove.

Is there a way of removing the "Installed (manual)" flag from all packages? If I could do this, all packages that do not belong to the core Ubuntu system should show up as "Installed (auto removable)" and I could individually mark only those as manually installed that I really still need and let apt/synaptic uninstall everything else.

I know that with today's hard disks, disk usage of installed packages is not an issue. But those packages accumulate over time and need to be updated with every security update and every ubuntu dist-upgrade, wasting time and bandwidth.

---

### Post by slakkie on 2010-01-05
sudo aptitude markauto <package> <package2>

Watch out though, if you mark a package as auto and it has no dependencies with another package it will remove that package!

---

### Post by Prendi on 2010-01-05
cool, that's what I was looking for. 
```
aptitude search '?installed'
```
Gives me a list of all installed packages, which can be filtered using OpenOffice Calc's csv importer, and then fed into
```
sudo aptitude markauto --schedule-only
```
(the last parameter prevents the instant removal of all installed packages!)

I would not recommend it as a general measure, though, since you need to know what packages (apart from ubuntu-desktop) to re-mark as manually installed.

---

