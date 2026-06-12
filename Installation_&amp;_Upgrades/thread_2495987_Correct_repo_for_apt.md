---
title: "Correct repo for apt"
date: 2024-03-11
forum: Installation &amp; Upgrades
---

### Post by bezrobotnyjoe on 2024-03-11
Hey guys,

Ive just checked my /etc/apt/sources.list and this what I see:


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates main restricted
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates universe
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-backports main restricted universe multiverse
# deb-src [http://pl.archive.ubuntu.com/ubuntu](http://pl.archive.ubuntu.com/ubuntu) lunar-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lunar-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lunar-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lunar-security multiverse

Whats about this archive repos? They should be there? Is it safe?

Thanks

---

### Post by ajgreeny on 2024-03-11
You have a strange mix of repos for mantic (the enabled repos) and lunar (all the disabled source repos).
Have you manually edited the sources.list file to try to make changes for some reason?

Which version do you think you are using as it looks as if mantic 23.10 is the one that is being used.
Perhaps you have carried out a version upgrade from lunar 23.04, to mantic 23.10?

Give us all the details and also show us the complete terminal output, using code tags please, of command
**sudo apt update**
There is a **how-to** for code tags in my signature below.

---

### Post by bezrobotnyjoe on 2024-03-11
Yes I did upgrade from 23.04 to 23.10 and no I didnt touch that file manualy.

Old:1 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease
Old:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic InRelease
Old:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates InRelease
Old:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-backports InRelease
Downloadig:6 [https://mega.nz/linux/repo/xUbuntu_23.04](https://mega.nz/linux/repo/xUbuntu_23.04) ./ InRelease [2&#8239;961 B]                                   
Old:7 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease                                          
Old:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security InRelease
Old:5 [https://packages.microsoft.com/repos/code](https://packages.microsoft.com/repos/code) stable InRelease
Downloaded 2&#8239;961 B w 2s (1&#8239;899 B/s)

Is there any list of correct official repos for 23.10?

---

