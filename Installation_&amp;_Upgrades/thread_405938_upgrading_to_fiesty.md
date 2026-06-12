---
title: "upgrading to fiesty"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2007-04-10
Hey,

I am trying to upgrade from edgy to fiesty!

When i try doing an 'update-manager -c -d', it shows me this

**"Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)"**

my net connection is fine...does this happen because the server from which download is happening is down for some maintaining purpose or something...or is it something with my repo...

this is my source.list

> 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe
 multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univ
erse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
#deb [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free
#deb-src [http://packages.freecontrib.org/plf](http://packages.freecontrib.org/plf) edgy free non-free

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main universe restricted multiverse

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main


---

### Post by ittiam on 2007-04-10
i got around that.

But i have a new problem...while it is trying to install new set of packages..it is giving me..."impossible in install this package (kubuntu-desktop). file this as bug report"...

any idea what cud the reason be?

---

### Post by bulldog on 2007-04-10
Not really,no.:) 

Did you installed applications from 'other' repo's beside the ubuntu repo's?
This can make the upgrade fail,because only application from within the official repositories will be upgraded,the 'strange' applications can't be upgraded because the repo's aren't in your sources.list.

---

### Post by kealan on 2007-04-24
> **ittiam said:**
> i got around that.

But i have a new problem...while it is trying to install new set of packages..it is giving me..."impossible in install this package (kubuntu-desktop). file this as bug report"...

any idea what cud the reason be?

I'm having the exact same problem, it would be great if you would explain what you did.

---

