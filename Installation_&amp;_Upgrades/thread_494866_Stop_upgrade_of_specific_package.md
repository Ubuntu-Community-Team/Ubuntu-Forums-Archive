---
title: "Stop upgrade of specific package"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by brk3 on 2007-07-07
I recently downloaded the amarok source package from the Ubuntu repositories, made one or 2 source changes, rebuilt and installed it.
This all worked fine, however the little orange update icon is now constantly sitting in my tray asking me to 'update' amaork.
Even though the one I have installed is the same version, it somehow seems to be detecting it is not the real one.  Is there anyway to stop being asked to upgrade this package without just disabling the whole backports repository from where it originates?

---

### Post by bmorency on 2007-07-07
I think what  you are looking for is the program dselect. 

open a terminal and type:

sudo dselect
select the 'select' menu
then hit 'q' to exit the help.

it will bring up a menu of all installed packages.

hit '/' to bring up the search function.

type in 'amarok'
highlight amarok and hit the '=' button
highlight amarok-xine and hit the '=' button

it will put those two packages on hold from being updated.

hit enter and you should be at the main menu. then quit.

hope that works for you.

---

### Post by brk3 on 2007-07-14
That did it thanks very much! Never even heard of that utility before :)

---

### Post by pezplaya on 2007-10-26
thanks, that worked for me too.  I needed to hold back wine from being updated because office 2003 only works with a specific version of wine on my system.

---

### Post by zvacet on 2007-10-26
You can do the same with synaptic.Mark your package wich you don´t want to be upgraded>package>lock version

---

