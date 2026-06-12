---
title: "Error upgrading from Hardy to Intrepid."
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by Uriel2006 on 2008-11-20
Hello all,

i tried to upgrade from 8.04 to 8.10 today, using the network method.

Both the upgrade manager and the command line interface are stoping with the following error:

W:Failed to fetch [http://archive.canonical.com/dists/intrepid/Release](http://archive.canonical.com/dists/intrepid/Release) 
Unable to find expected entry partnerdeb/binary-i386/Packages in 
Meta-index file (malformed Release file?) 

Problem is i am able to download the "Release" file from this url, and it looks fine to me.

What's happening ?

Uriel

---

### Post by Partyboi2 on 2008-11-20
Could you post your sources.list please, open a terminal and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by Uriel2006 on 2008-11-21
> **Partyboi2 said:**
> Could you post your sources.list please, open a terminal and post the output to
```
cat /etc/apt/sources.list
```



Hello,

after i tried to upgrade, it is:

deb [http://archive.canonical.com/](http://archive.canonical.com/) intrepid partner
deb [http://ppa.launchpad.net/mvo/ubuntu](http://ppa.launchpad.net/mvo/ubuntu) hardy main
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) intrepid-security main restricted universe multiverse
deb [http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) intrepid-updates main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-backports restricted main multiverse universe #Added by software-properties
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-proposed restricted main multiverse universe #Added by software-properties
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe #Added by software-properties
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main universe #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu](http://ubuntu.uni-klu.ac.at/ubuntu) intrepid-security main restricted universe multiverse
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu](http://ubuntu.uni-klu.ac.at/ubuntu) intrepid-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

anyway, i downloaded the CD, mounted it as a loop device, and then i'm upgrading while writing right now....

but using the internet, it doesn't works.


Uriel

---

