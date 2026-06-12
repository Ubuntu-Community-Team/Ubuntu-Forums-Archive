---
title: "Deluge Install problem"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by apauloisdead on 2007-10-07
I tried my best searching around and trying to solve this problem myself, but i can't seem to fix it. 

I'm trying to get Deluge to install, but this is my 2nd day with linux, so i really barely have a clue what i'm doing. After a few searches i downloaded a package installer from GetDeb. Now when i run it i get the error:


Error: Dependency is not satisfiable. libboost-date-time1.34.1

I've already ran this in terminal:

sudo apt-get install g++ python-all-dev python-all python-dbus python-gtk2 python-xdg python-support libboost-dev libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev libboost-serialization-dev libssl-dev zlib1g-dev

...and i already ran this, which i found in the forums:

sudo apt-get install python-notify notification-daemon

I did a quick google search and ended up here:

[http://packages.debian.org/sid/libboost-date-time1.34.1/i386/download](http://packages.debian.org/sid/libboost-date-time1.34.1/i386/download)

...but they don't recommend manually downloading and installing from their website, and me being the total noob, i don't feel confortable doing that any ways.


Now please go easy on me, as i said i really am trying my best to get a feel for linux, but can anyone help me?



Edit: Ok i solved it, i downloaded the deluge for gutsy, i have fiesty.

WHOOPS.

---

