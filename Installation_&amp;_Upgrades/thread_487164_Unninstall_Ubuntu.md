---
title: "Unninstall Ubuntu"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by cuervo_jones_85 on 2007-06-28
Hello folks,
so i installed ubuntu on my girlfriends laptop (dual boot with XP) and she doesn't want it anymore.. go figure ;) but the catch is.. her XP is full of problems and need to be reinstalled also.. and she can't backup her files wich are on windows.

beautiful isn't it?!

so i want to format the linux partition to fat32 so i can put her files there and then reinstall windows, but how do i format or unninstall ubuntu without damaging the MBR?

suggestions are welcome!

---

### Post by mikewhatever on 2007-06-28
Herman's site has a good page [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by vexorian on 2007-06-28
You don't really have to worry about the MBR, keep her files in a separate fat32 partition (which seems to be your plan) and install XP to another partition, it will make its own MBR and then "My computer" will probably display the fat32 partition as D:

---

