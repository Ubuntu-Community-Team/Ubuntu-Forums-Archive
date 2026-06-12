---
title: "Repackage programs to &amp; install from cd"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by BigSteve_G on 2010-02-04
Anyone know of an easy & practical way to re-package (in to debs) all the programs I have installed on a system so I can copy them on to a disc & install on another machine?
Basicaly so I only ever download the programs I want once but can install them as often as I need.

I'm sure I read that by just copying the /usr directory to a target machine may work (although I haven't tried I doubt it). I've also read that it may be possable to simply copy a whole Ubuntu installation to another drive & use it in another machine.

-Any ideas?

---

### Post by Leppie on 2010-02-04
if you do not use "apt-get clean" you can find the downloaded .deb packages here:
```
/var/cache/apt/archives/ 
```

copy the packages to cd/dvd and install on another machine using gdebi or dpkg (or even synaptic).

---

### Post by BigSteve_G on 2010-02-26
FYI

Managed to do it thanks Synaptic Package Manager & the info found at;
[COLOR=Blue]https://help.ubuntu.com/community/InstallingSoftware#Aptitude - the text-based method[/COLOR]

---

