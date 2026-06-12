---
title: "weird java problems"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by dclaridge on 2005-07-26
I have been trying to figure out how to install the JRE/JDK on ubuntu, and from what I've read i must simply use the following comands after downloading the JDK .bin file from sun.com

```
sudo apt-get install java-package fakeroot
fakeroot make-jpkg jdk-1_5_0_02-linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update02_i386.deb
```

this is all very nice but the first line returns the following:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package java-package
```

I have enabled all the repositories (except the ubuntu CD) through synatpic so this isn't the problem - - has this package just disappeared off the face of the earth? Is there an alternative way to get Java working.

Bye the way, it seems very odd for an OS not to have a JRE preinstalled, to allow ordinary java applications to run??? Why isn't one part of Ubuntu? All the other major distributions run java apps out of the box...

---

### Post by dclaridge on 2005-07-26
ah nevamind - its in 'multiverse'... didnt add that one

geez its slow downloading off multi :S

---

### Post by Tortured-x on 2005-07-26
good work.

on the off note...


AUSSIE AUSSIE AUSSIE!!!

---

### Post by dclaridge on 2005-07-26
[QUOTE=Tortured-x]good work.

on the off note...


AUSSIE AUSSIE AUSSIE!!![/QUOTE]
 OI! OI! OI!

---

