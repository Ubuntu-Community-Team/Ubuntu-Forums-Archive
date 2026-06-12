---
title: "Update Manager fails"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by mzar on 2007-12-03
Hi all,

I got problem when using apt-get update. I got those error.

```
E: Malformed line 1 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

This is my source list.

```
## Major bug fix updates produced after the final release of the
## distribution.
deb http://my.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://my.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://my.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://my.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://my.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

```

I dont know what wrong. Anyone knows what wrong? :confused:

---

### Post by zvacet on 2007-12-04
Try [this](http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories) source list.

---

