---
title: "Uninstalling / Removing stuff"
date: 2005-03-31
forum: Installation &amp; Upgrades
---

### Post by Dracontopes on 2005-03-31
In Windows you could easily use a uninstaller that came with the game. Now I have Doom 3 installed, but I want it removed from my system.

What do I do to completely remove Doom 3 from my HD / System?

Oh and, how do I uninstall/remove nforce2 drivers from the HD?

---

### Post by lao_V on 2005-03-31
simple: in terminal type sudo apt-get remove *package-name*

---

### Post by Dracontopes on 2005-03-31
[QUOTE=lao_V]simple: in terminal type sudo apt-get remove *package-name*[/QUOTE]
 The nforce2 drivers and doom3 were not installed using apt-get or synaptic and also were not .deb packages. So that command doesn't work, saying can't find package :(

---

### Post by arctic on 2005-03-31
so, did you install a tar.gz file in your /home directory without writing anything to your /usr folder? in this case, all installation files are in your /home folder and can be removed by simply draggin' them to the dustbin. ;)

---

### Post by nikopol on 2005-03-31
[QUOTE=Dracontopes]The nforce2 drivers and doom3 were not installed using apt-get or synaptic and also were not .deb packages. So that command doesn't work, saying can't find package :([/QUOTE]
 No easy answer to that one - most likely however the Doom3 stuff will all be in one folder (/usr/local/games/Doom3 maybe?). Deleting that folder will get you rid of the programs files. does Doom3 have a Linux removal program integrated? (I don't know - never played it :) )

---

### Post by Dracontopes on 2005-03-31
I found where doom3 placed his files, so I guess it's safe to just delete them? :P No registry that will get screwed up etc ^_^

And the nvidia drivers, I removed the nvsound.ko and nvet.ko
Hope this will work...

---

### Post by arctic on 2005-03-31
take a look at this before you continue. a small guide for beginners. :)
[http://linuxreviews.org/beginner/](http://linuxreviews.org/beginner/)

---

