---
title: "I need help installing WineHQ..."
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by 1337 Killer on 2006-09-01
Alright, well, I just installed Ubuntu yesterday and I'm just getting the hang of it. It's my first Linux Client. I searched Wine in the Synaptic Package Manager and it came with no results. Can someone tell me how to fix this. I'm really confuse :confused:

---

### Post by croak77 on 2006-09-01
It's in universe so it should be there. What happens when you open a terminal and type;
```
sudo aptitude update
sudo aptitude install wine
```

---

### Post by 1337 Killer on 2006-09-01
I typed those, and I still don't have it. This is what happened:

This is not the whole thing btw...
```
No candidate version found for wine
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by croak77 on 2006-09-01
OK. Can you post your /etc/apt/sources.list.

---

### Post by 1337 Killer on 2006-09-01
I just checked when trying to get VideoLAN Media Player. I don't have any Universe mirrors. Where do I get them? I've got nothing in that folder.

---

### Post by croak77 on 2006-09-01
```
 ## All officially supported packages, including security- and other updates
 deb http://archive.ubuntu.com/ubuntu dapper main restricted
 deb http://security.ubuntu.com/ubuntu dapper-security main restricted
 deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 
 ## The source packages (only needed to recompile existing packages)
 #deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
 #deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
 #deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 
 ## All community supported packages, including security- and other updates
 deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
 deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
 deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
 
 ## The source packages (only needed to recompile existing packages)
 #deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
 #deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
 #deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse

```

---

