---
title: "installing virtualbox, problems."
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by patrickmclennan on 2010-01-25
alright, so i have a 2nd gen. ipod touch and ubuntu 9.04, and from what i've gathered my only options to update it would be to either get wine or virtual box and run windows OR jailbreak it.  for various reasons, i'd rather not jailbreak it, and i attempted to run virtualbox but i ran into some problems.

i installed windows xp on virtual box and everything ran great, but i found out that i had the OSE version of it, and only the PUEL version has usb compatibility (which i would obviously need to use my ipod).  i uninstalled the OSE version, and then tried to download and install the PUEL version but i get a message saying "only one software management tool is allowed to run at the same time.  Please close the other appilication e.g. 'update manager'.." i am the only person who is logged in and i only have only firefox and this package installer window open, so i'm not sure what software management is running, or how i would even close it.

as well, whenever i try to open synaptic i get this message "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

i assume these problems are related, seeing as i was using both programs flawlessly before i uninstalled virtualbox.  any help would be much, MUCH appreciated.  thanks!

---

### Post by byStanderone on 2010-01-25
...you can run sudo dpkg --reconfigure -a that would correct the failed install/uninstall. should there be a broken file, you  can then fix it thru synaptic after you've done the sudo thing above.

---

### Post by patrickmclennan on 2010-01-25
done! problem solved.  haha, pretty easy fix, i'm an ubuntu noob so even the simplest problems leave me clueless.

thanks so much, REALLY appreciated! this can be locked or whatever now.

---

