---
title: "repositoty help"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by kiiz on 2008-01-09
i use kpackage instead of adept.however i need the address for the repository for normal application and updates so i can manual enter them in kpackage

---

### Post by codesplice on 2008-01-09
From my /etc/apt/sources.list:

```


## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Gutsy (Ubuntu 7.10) +++
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse

## +++ Backports & Proposed (Ubuntu Unstable) +++
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted universe multiverse

## +++ Source Repositories +++
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```

This what you're looking for?

---

