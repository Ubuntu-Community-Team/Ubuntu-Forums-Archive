---
title: "Efty Edge Upgrade Failed"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by billbog on 2008-09-10
Hi bit of a noob here .Having to reinstall Ubuntu after HD failure -  my Efty Edge Upgrade has failed .Get this message "Authenticating the upgrade failed . Check Network connection & correct writing of repository address in preferences. How do I do this.

---

### Post by pay on 2008-09-10
open the terminal and type ```
sudo nano /etc/apt/source.list
```and make sure it looks sane. Or replace it with this ```
deb http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu edgy partner
deb-src http://archive.canonical.com/ubuntu edgy partner
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
```then ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by billbog on 2008-09-10
No - I am still getting the same problem . When I try to upgrade i get ; 
Authenticating the upgrade failed .Could be problem with network or server and : 
Could not download all repository indexes and 

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---

### Post by billbog on 2008-09-10
Further to last posting. 
sudo nano /etc/apt/source.list said file had been modified and so tried your alternative but no luck

---

### Post by billbog on 2008-09-11
Nearly upgraded but get this:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/multiverse/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 194.169.254.10 80]
Any ideas ?

---

### Post by tuxerman on 2008-09-11
Don't wanna be nitpicking in here, but it's Edgy Eft and not Efty Edge. Or did you mean to put it that way? :lolflag:

---

### Post by billbog on 2008-09-11
Yes Edgy Eft thanks :(

---

