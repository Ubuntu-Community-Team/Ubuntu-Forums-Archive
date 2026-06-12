---
title: "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Imoen_tw on 2007-12-11
I try the code sudo apt-get install ubuntu-desktop and it tells me "Unable to fetch some archives, maybe run apt-get update or try with --fix-missing".

Then I try sudo apt-get install vsftpd and it tells me the same, so I try sudo apt-get -f install vsftpd and again the same. All of them are Temporary failure resolving 'us.archive.ubuntu.com'.

What am I doing wrong and how do I fix this?

---

### Post by PmDematagoda on 2007-12-11
Do:-

```
sudo apt-get update
```

and post the result you get.

Also post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by Imoen_tw on 2007-12-11
sudo apt-get update
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/translation-en_US.bz2) Temporary failure resolving 'us.archive.ubuntu.com'

There are many lines of this with the part after dists being different on each line. 

cat /etc/apt/sources.list
Starting at what I can see on my screen because I don't know how to make it move up:
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main restricted
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main restricted
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main universe
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main multiverse
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-security main multiverse

---

### Post by PmDematagoda on 2007-12-12
Try changing the location of the server by going to Software Sources in System>Administration>Software Sources, that might fix the problem.

---

### Post by Imoen_tw on 2007-12-12
> **PmDematagoda said:**
> Try changing the location of the server by going to Software Sources in System>Administration>Software Sources, that might fix the problem.

What do I change them to? I tried germany and UK and get the same error. (btw, I am trying this in shell with nano, I don't have a desktop installed because of this issue installing it.)

---

