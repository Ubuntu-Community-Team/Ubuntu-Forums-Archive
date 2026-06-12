---
title: "Errors!! Please help!!"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by pinkypinkpink on 2011-05-16
Ok, so my first error would be my Synaptic Package Manager.... whenever I attempt to open it, it gives me an error stating..

"E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-updates_main_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."


My second error is my Ubuntu Software Center not being able to load itself... it's showing the loading icon on my cursor, then it vanishes, and doesn't load.

None of this begin to happen until recently... and randomly.

---

### Post by dino99 on 2011-05-16
open a terminal and run:

sudo rm /var/lib/apt/lists/*
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

