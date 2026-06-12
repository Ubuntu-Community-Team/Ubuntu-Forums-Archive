---
title: "Missing libxine-extracodecs from multiverse"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by Freddy on 2006-07-17
Hi all, feels good to be back on Kubuntu after some 6 mounths of scouting ;-).

I've tried to setup mp3 support on my new install but I've hit a wall, when trying to install libxine-extracodecs from multiverse, apt-get only tells me that some of my other packages point towards that package but that it doesn't exist one.

Can someone pls tell me whats wrong or point me to a site where I can download the package maunally. 

Thanks. /// Freddan

Maybe it's a sources problem, so I'll post mine aswell.

```
## STANDARD REPOS, ALL UNCHECKED

deb cdrom:[Kubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb http://se.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Universe
deb http://se.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper universe

## Backports.
deb http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

## Security.
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

## MY OWN INPUTS

## Dapper-commercial by canonical.
## currently has realplay (realplayer 10) and opera (opera 9).
deb http://archive.canonical.com/ubuntu dapper-commercial main

## Cipherfunk multimedia packages (GPG key: 33BAC1B3).
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main
deb-src ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

## Bleeding edge (official) wine repository for Dapper.
## only uncomment it if you need it.
## deb http://wine.budgetdedicated.com/apt dapper main
## deb-src http://wine.budgetdedicated.com/apt dapper main

## skype (official).
## only uncomment it if you need it
## deb http://download.skype.com/linux/repos/debian/ stable non-free

## Amarok 1.4.1.
deb http://kubuntu.org/packages/amarok-141 dapper main
```

---

### Post by matthew on 2006-07-17
Hi, Freddan, welcome back!

Add this to your sources.list```
## Multiverse
deb http://se.archive.ubuntu.com/ubuntu/ dapper multiverse
deb-src http://se.archive.ubuntu.com/ubuntu/ dapper multiverse
```

---

### Post by Freddy on 2006-07-17
Hi matthew. 

Thanks for the help, that did the trick :-).   /// Freddan

---

