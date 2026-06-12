---
title: "apt-get package name"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by doc_holiday on 2005-07-28
I've just installed ubuntu in server mode. Now I need to install some extra packages, is there a way with apt-get to search for the name as you can do in synaptic?

thanks

---

### Post by jasmuz on 2005-07-28
to search: sudo apt-cache search packagename

to install: sudo apt-get install packagename

---

### Post by SFN on 2005-07-28
apt-cache search *filename* 

Any part of the filename will work. For example, "apt-cache search xmms" will give you everything that has xmms in the name or description.

---

### Post by angkor on 2005-07-28
In addition, the following are also quite useful:

apt-cache show [pkg]---------------- for long description of the package

apt-cache policy [pkg]--------------- to see what version is available and what version you have installed

apt-cache depends [pkg]-----------to see all dependencies and suggested packages


There are more but these are the ones I use most.

---

### Post by PMO6022 on 2005-07-28
Alternatively you could learn to use **dselect** - a command line frontend to apt-get.  Very powerful once you get the hang of it.

*[edit : thanks *[color=black]*[ ]("member.php?u=17736")angkor]*
[/color]

---

### Post by Sam on 2005-07-28
[QUOTE=jasmuz]to search: sudo apt-cache search packagename

to install: sudo apt-get install packagename[/QUOTE]
apt-cache doesn't need sudo !

---

### Post by angkor on 2005-07-28
[QUOTE=PMO6022]Alternatively you could learn to use **deselect** - a command line frontend to apt-get.  Very powerful once you get the hang of it.[/QUOTE]

edit: that's **dselect** ;)

---

