---
title: "removing package from synaptic package manager"
date: 2017-09-02
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2017-09-02
[LIST=1]
[*]I've added a PPA to get the version of a media player I want
[*]I installed the media player and realized that it has a bug
[*]I removed the PPA by deleting the reference in /etc/apt/sources.list.d
[*]I then used the the package manager to completely remove the package
[*]When I search for the media player in the package manager, it still shows up. This prevents me from installing another version of this player
[/LIST]

How can I remove all references to this package?

Thanks

---

### Post by ian-weisser on 2017-09-02
After deleting the PPA source entry,
and after uninstalling the package(s),
did you refresh apt's package database (sudo apt update)?

---

### Post by lister171254 on 2017-09-03
Yes

---

### Post by westie457 on 2017-09-03
Have you tried ```
sudo apt clean
sudo apt autoclean
```?

---

### Post by linuxissuperawesome on 2017-09-03
Have You Tried Purging ```
sudo apt-get purge <packagename>
```?

---

### Post by lister171254 on 2017-09-03
Yes 
Have tried all the above suggestions, but the package still shows up

---

### Post by lister171254 on 2017-09-03
As so oftern, the problem is in the chair.

I checked the default Ubuntu package on another installation and it's the same version as the one from the PPA. 
Sorry to have wasted your time

---

