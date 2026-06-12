---
title: "update manager"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by thefuneralafterparty on 2010-07-08
Hello, new to ubuntu and somethings up with my update manager. theres an alert icon in the right hand corner and its bugging me.. it has the the following error message:



Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list, E:The list of sources could not be read.'




...Also, its not letting me add/remove software through the command line nor software center. ANY IDEAS, SMART PEOPLE???

---

### Post by davidmohammed on 2010-07-08
suggest 

sudo nano /etc/apt/sources.list

look through that file

add a # at the beginning of the line that has "wine-ppa" embedded in it

save

sudo apt-get update

---

### Post by plucky on 2010-07-08
> 'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list, E:The list of sources could not be read.'


The file is in directory /etc/apr/sources.list.d and is called ubuntu-wine-ppa-lucid.list

To see what the file contains ```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
```

to edit the file ```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-lucid.list
``` and remove the n in line 2

Or just un-tick the box in **Software Sources**

Good Luck

---

### Post by thefuneralafterparty on 2010-07-08
thanks david and plucky. problem: solved

---

