---
title: "apt-get update"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by hudelfa on 2006-09-12
Hello everybody first;

When I want to update my ubuntu from console I write "apt-get update" it fetched packets but at the end it gives an error reads "Fetched 169kB in 11s (15.1kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


HOW CAN I FIX THIS PROBLEM.

THANKS IN ADVANCE...
"

---

### Post by Anonii on 2006-09-12
> **hudelfa said:**
> Hello everybody first;

When I want to update my ubuntu from console I write "apt-get update" it fetched packets but at the end it gives an error reads "Fetched 169kB in 11s (15.1kB/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


HOW CAN I FIX THIS PROBLEM.

THANKS IN ADVANCE...
"
Execute:
**cat /etc/apt/sources.list**
in the temrinal.
And paste here the output.

---

### Post by hudelfa on 2006-09-13
Ok.I am not in front of my computer now.I am going to do it tonight.

THANKS...

---

### Post by unisol on 2006-09-13
when i do sudo apt-get update it downloads from repos but in the end i get message error with gzip some updates ignored older ones used. i have edited /etc/apt/sources.lst and still get message

---

### Post by hudelfa on 2006-09-13
this is the output!! Anonii

deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe  multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted unive rse multiverse
 deb-src [http://tr.archive.ubuntu.com/ubuntu/](http://tr.archive.ubuntu.com/ubuntu/) dapper-backports main restricted u niverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by onioneater36 on 2006-09-13
bump

---

