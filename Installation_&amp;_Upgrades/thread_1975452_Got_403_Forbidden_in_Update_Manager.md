---
title: "Got 403 Forbidden in Update Manager"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by pitpet on 2012-05-07
Hi guys:

I got the following errors while press "check" button in update manager
They looks strange since they actually are in-accessible urls, for example:
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources) [COLOR="Red"]does not exists![/COLOR]
however
[http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources.gz) [COLOR="red"]does exists![/COLOR]


==================================================
/etc/apt/source.list
==================================================
cat /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse #Added by software-properties


==================================================
Error Code:
==================================================

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  403  Forbidden
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  403  Forbidden
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I've been working on this issue for more than 3 hours and still got no progress. :-(
Any help will be appreciated!

---

### Post by pitpet on 2012-05-08
Anybody could help? thanks !

---

### Post by dino99 on 2012-05-08
your sources.list is borked, replace with the lines below (copy & paste to avoid errors):

sudo gedit /etc/apt/sources.list

- erase everything and copy/paste:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-proposed main universe restricted multiverse

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric free non-free

- save and close that sources.list file
- then update & enjoy ):P

---

