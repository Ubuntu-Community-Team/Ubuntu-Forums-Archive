---
title: "sources.list required for 7.10 gutsy"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by mincho on 2007-10-29
what sources.list i use to update my gutsy :( please post your list here :(...

---

### Post by taurus on 2007-10-29
```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu gutsy universe
deb-src http://archive.ubuntu.com/ubuntu gutsy universe

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://archive.ubuntu.com/ubuntu gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy multiverse

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu gutsy-commercial main 

```

---

### Post by larryalk on 2007-10-29
When I add the 'gutsy-commercial main' to the stock gutsy 
sources.list I get
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy-commercial/main/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

This was the addition in my sources.list:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

Is this just a temporary thing?

Larryalk

---

### Post by taurus on 2007-10-29
Edit your /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of that line to comment it out.  Then, run those two commands again.

```
sudo apt-get update
sudo apt-get upgrade
```

---

