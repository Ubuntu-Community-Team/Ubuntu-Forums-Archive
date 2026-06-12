---
title: "Problem with Gutsy Upgrade. Network Fetching Problem."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by BnetTheAwesome on 2007-10-21
Here is the message I get whenever I try to upgrade to Gutsy.

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz) 404 Not Found
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]"

Please help. I want to get Gutsy ASAP.

---

### Post by BnetTheAwesome on 2007-10-21
Someone help. I want Gutsy up soon, hopefully today.

---

### Post by BnetTheAwesome on 2007-10-21
No responses yet it seems. Here is something more to help.

I thought that you could do a apt-dist upgrade for this, so I went in to that services file or whatever it's called and changed all instances of "edgy" and "feisty" to "gutsy".

Plz help.

---

### Post by CapPicard on 2007-10-22
> **BnetTheAwesome said:**
> Here is the message I get whenever I try to upgrade to Gutsy.

"A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/gutsy/eyecandy/source/Sources.gz) 404 Not Found
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/binary-i386/Packages.gz) 404 Not Found [IP: 195.114.19.35 80]
Failed to fetch [http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz](http://ubuntu.beryl-project.org/dists/gutsy/main/source/Sources.gz) 404 Not Found [IP: 195.114.19.35 80]"

Please help. I want to get Gutsy ASAP.

Edit your /etc/apt/sources.list and comment out those lines with those URLs. (just put a # in front). Then, attempt the upgrade again. It should let you go further. Once you're upgraded, you can try removing the hash marks and upgrade those if possible.
:guitar:

---

