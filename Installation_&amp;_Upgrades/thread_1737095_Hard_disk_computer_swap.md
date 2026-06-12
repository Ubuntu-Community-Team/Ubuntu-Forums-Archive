---
title: "Hard disk computer swap"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by Losergamer04 on 2011-04-23
Sorry if this was already covered in a forum before but I didn't see anything in my search.

Anyways, we purchased a new laptop for my wife and we want to swap the hard drive to the new laptop.  I swapped video cards once on my desktop and it didn't go so well...  Is there a way to have the drivers "reset" or reconfigure the OS to default so we don't have to go through the hassle of installing everything all over again?  Something like a boot -r on an OpenBoot PROM would be nice if there is such a feature in Ubuntu.

---

### Post by Joe of loath on 2011-04-23
All the drivers in Linux are kernel mode. Plugging the hard disk into another PC should 'Just Work', at least unless you've installed custom drivers. Video cards are the worst, as you've experienced before. If you have any proprietary video drivers installed, uninstall them first.

---

