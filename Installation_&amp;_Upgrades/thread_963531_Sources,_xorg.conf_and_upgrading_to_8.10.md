---
title: "Sources, xorg.conf and upgrading to 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Confuzius on 2008-10-30
I have a few 3rd party sources in my sources list (wine, mediabuntu, screenlets, etc)  Should I change all of these to intrepid sources before the upgrade, remove them completely or deal with them after the upgrade.

Also I've finally got my xorg.conf the way I like it, with my dual displays and all the different settings needed to disable the second monitor on playing full screen 3d games.  Will this still work with the new xorg if I back this up and replace it after the upgrade, or will it just change what's necessary and leave my customer settings as is?

---

### Post by ddrichardson on 2008-10-31
This is just my opinion but I'd disable the 3rd party repos before upgrading then re-enable afterwards to avoid any conflicts that will be hard to get assistance for, then re-enable and check for updates afterwards.

According to the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/810") its only the input device entries that are ignored as they are dealt with by input-hotplug.

---

