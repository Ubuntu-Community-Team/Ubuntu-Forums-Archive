---
title: "Trouble running Update Manager"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by Pappalnator on 2008-11-30
I am running Dell's 8.04.1 Ubuntu Distro for the Dell Mini 9

Update manager apparently can't locate its sources, thus wont update the files, thus will continue trying each time I press check.. Thus I cant update my OS -.- AHHH!!!

Help is appreciated!

Add't Info:

[COLOR="Blue"]Error Code Given By Update Manager[/COLOR]> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found [IP: 91.189.88.46 80]
Some index files failed to download, they have been ignored, or old ones used instead.

[COLOR="blue"]Observations While Running[/COLOR]
While running, I opened the See Individual File or similar tab. All I saw was 100+ files fly by in about 20 seconds showing either Hit or Miss (mostly Miss). It struck me odd that none of them actually loaded or installed, they just flew by.

[COLOR="blue"]My Prediction[/COLOR]
Im not fluent with Ubuntu yet, but I have a feeling it has something to do with Error: (404 Not Found) up in the Error Code U.M. gave me. Possibly the sources are wrong or the sources are down? 
[COLOR="blue"]
Computer Status While Running[/COLOR]
 >  Plugged In
 >  Fully Connected to Internet (Speedy too!)


Thanks again doods!

---

### Post by Pumalite on 2008-11-30
Check your connection and/or change Server
It would help:
cat /etc/apt/sources.list

---

### Post by Pappalnator on 2008-11-30
Results from cat /etc/apt/sources.list are as follows:

> deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy restricted multiverse universe main
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/netbook-remix-team/ubuntu](http://ppa.launchpad.net/netbook-remix-team/ubuntu) hardy main

---

### Post by Pumalite on 2008-11-30
I'd try to find the 'Best Server'.
[http://www.ubuntumini.com/2008/10/check-out-dells-mini-9-repositories.html](http://www.ubuntumini.com/2008/10/check-out-dells-mini-9-repositories.html)

---

### Post by Pappalnator on 2008-11-30
Thank you very much, Ill play around with this.

Anyone know if updating via Update Manager to Intrepid Ibex will delete any of my current data?

Thanx.

---

### Post by Pappalnator on 2008-11-30
Bump

Method did not work, continued to reject me

Any help is appreciated! please!

---

