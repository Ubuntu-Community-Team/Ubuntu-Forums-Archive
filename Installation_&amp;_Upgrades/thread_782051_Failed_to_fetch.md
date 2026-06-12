---
title: "Failed to fetch"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Xoanan on 2008-05-04
HI All

I have been having some issues with the updates as well as having some issues with jre.

I keep getting this error on updates

```
failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Any ideas on this one?

---

### Post by Xoanan on 2008-05-04
Here's the sources list

```
 
# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Xubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted multiverse web
deb-src http://archive.ubuntu.com/ubuntu/ hardy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted multiverse web
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates restricted main multiverse universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb http://wine.budgetdedicated.com/apt edgy main
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse


deb http://archive.ubuntu.com/ubuntu/ hardy-security main restricted multiverse web
deb-src http://archive.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu edgy-security universe
deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.canonical.com/ubuntu hardy partner
deb http://packages.medibuntu.org/ hardy free non-free
deb http://archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe web

```

---

### Post by Xoanan on 2008-05-08
Possible fix here

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/204691/]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/204691/")

I will try it and let you know

:popcorn:

---

### Post by bapoumba on 2008-05-08
Yes, please remove the two words "web" from your sources.list.

---

### Post by Xoanan on 2008-05-08
Thanx!  That worked!  Issue resolved!

---

### Post by bapoumba on 2008-05-09
Glad to see you got it to work, congrats :)

---

