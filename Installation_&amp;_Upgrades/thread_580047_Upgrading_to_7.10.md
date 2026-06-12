---
title: "Upgrading to 7.10"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by kshymkiw on 2007-10-18
I am attempting to perform the upgrade from Feisty to Gutsy.  I am receiving some errors and I was wondering if I could receive some help:

In my main.log file this is the only errors I have

```
2007-10-18 16:45:26,476 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'
```

I don't see any more errors in the logs.  Anyone have any suggestions?

I have used Automatix in the past and I am wondering if the sources for that are hurting the upgrade process.

---

### Post by jetpeach on 2007-10-18
i have similar error in kubuntu and have never used automatix on this machine.
i read to try "aptitude search ~ahold" to search for any held packages, but i don't have any held packages. i don't have any broken ones either.

hoping for a solution,

---

### Post by superyounan1 on 2007-10-18
automatix is notorious for messing things up in ubunu, avoid it

try
```

sudo apt-get install -f
sudo apt-get autoclean

```

open synaptic and use it to disbale all 3rd party repositories, then do

if you have compiz fusion running in feisty, remove it so you get the new version straight out of ubuntu's own repository:
```

sudo echo "Removing old compiz things (ask for sudo password now, so commands won't be interupted later)"
echo "aptitude -y remove" `sudo dpkg -l | egrep '(beryl|emerald|compiz)'| awk '{print $2}'` | sudo bash

```

```

sudo apt-get -y update
sudo apt-get -y dist-upgrade

```

if you did have compiz fusion and you removed it, the ubuntu-desktop metapackage was probably removed one time or another
```

sudo apt-get -y install ubuntu-desktop

```

now try to update again
```
gksudo update-manager -c
```

---

