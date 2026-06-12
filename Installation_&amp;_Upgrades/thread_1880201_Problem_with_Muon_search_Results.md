---
title: "Problem with Muon search Results"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by UsmanKhan on 2011-11-13
I have kubuntu 11.10 with muon as package manager.

when i enter name in search packages  are not shown although with manual scrolling in the list i found them listed in the packages.
I dont know what he problem with search result . any way to fix that??

I tried installing synaptic and same thing is happening to it also . I have to manually scroll and add packages.??

---

### Post by DesG on 2011-12-04
I have the same issue, if I type, for example virtualbox into the search field, it just displays blank search results, if I manually scroll down the list of available packages, I can install from there.

Seems like a strange search function ;)

---

### Post by adanos on 2012-01-13
Looks like i've had same issue and have solved it just by removing and installing again muon related packages.
Just try to make those 2 steps in terminal
```
1)sudo apt-get remove muon muon-installer muon-notifier muon-updater
2)sudo apt-get install muon muon-installer muon-notifier muon-updater
```
I've rebooted my laptop after each step just for case although dunno weather reboot is necessary)

---

### Post by scrub jay on 2012-01-21
> **DesG said:**
> I have the same issue, if I type, for example virtualbox into the search field, it just displays blank search results, if I manually scroll down the list of available packages, I can install from there.

I sometimes do a package search that shows a blank result and then realize that I don't have the proper filter selected. Then I'll switch over to "All" in the "By Category" filter or "All" in the "By Status" filter.

---

