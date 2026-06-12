---
title: "Uninstall package"
date: 2013-11-18
forum: Installation &amp; Upgrades
---

### Post by warellan on 2013-11-18
Hello,


[LIST=1]
[*]I manually installed SUMO 0.17.1 under Ubuntu 12.1 first ussing sudo add-apt-repository ppa:sumo/stable and later according to: [http://sumo-sim.org/wiki/Installing/Linux_Build#Manuall_install](http://sumo-sim.org/wiki/Installing/Linux_Build#Manuall_install). 
[*]I did not do any uninstall and as the package did not work as expected i repeated the second installation method several timesI. 
[*]Later I updated Ubuntu to 13.04 and 13.1. 
[*]Now I am trying to remove SUMO and used sudo apt-get --purge remove SUMO. After that  dpkg --list does not list SUMO. 
[*]The problem is SUMO still runs as if it has not been deleted. 
[*]I checked usr/local/bin and it has SUMO executables. 
[/LIST]

Help is highly appreciated.

Regards,

Wilmer

---

### Post by warellan on 2013-11-20
Solved.

[LIST=1]
[*]In Software & Updates: removed both PPA lines.
[*]In sumo-0.17.1 "sudo make uninstal", "make uninstall" alone would not work.
[/LIST]
Thank you,
Wilmer Arellano

---

