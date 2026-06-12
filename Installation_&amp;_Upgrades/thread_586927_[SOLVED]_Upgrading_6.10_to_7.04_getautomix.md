---
title: "[SOLVED] Upgrading 6.10 to 7.04 getautomix"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Xoanan on 2007-10-22
Hi All

I am attempting to upgrade from xubuntu 6.10 to xubuntu 7.04 and I am running into one little issue

This message shows up during the upgrade

Failed to fetch [http://www.getautomatix/com/apt/dists/edgy/Release.gpg](http://www.getautomatix/com/apt/dists/edgy/Release.gpg) Could not resolve 'www.getautomatix'
Failed to fetch [http://www.getautomatix/com/apt/dists/edgy/main/i18n/Translation-en_US.bz2](http://www.getautomatix/com/apt/dists/edgy/main/i18n/Translation-en_US.bz2) Could not resolve 'www.getautomatix'
Failed to fetch [http://www.getautomatix/com/apt/dists/edgy/main/binary-i386/Packages.gz](http://www.getautomatix/com/apt/dists/edgy/main/binary-i386/Packages.gz) Could not resolve 'www.getautomatix'

Thanx in advance:popcorn:

---

### Post by ddrichardson on 2007-10-22
There's a / where there should be a .```
http://www.getautomatix/com
```should be ```
http://www.getautomatix.com
```in /etc/apt/sources.lst

---

### Post by Xoanan on 2007-10-22
> **ddrichardson said:**
> There's a / where there should be a .```
http://www.getautomatix/com
```should be ```
http://www.getautomatix.com
```in /etc/apt/sources.lst

This is what I have that includes getautomix

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix/com/apt](http://www.getautomatix/com/apt) edgy main
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

When I attempted to add the 2 lines you mentioned, the update manager closed as soon as  I opened it.  I attempted with and without the "deb" prefix

---

### Post by Xoanan on 2007-10-22
> **ddrichardson said:**
> There's a / where there should be a .```
http://www.getautomatix/com
```should be ```
http://www.getautomatix.com
```in /etc/apt/sources.lst

This is what I have that includes getautomix

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix/com/apt](http://www.getautomatix/com/apt) edgy main
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy universe
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

When I attempted to add the 2 lines you mentioned, the update manager closed as soon as  I opened it.  I attempted with and without the "deb" prefix

---

### Post by ddrichardson on 2007-10-22
You don't need to add any lines, just change the one that says ```
 deb [http://www.getautomatix/com/apt](http://www.getautomatix/com/apt) edgy main
```To```
 deb [http://www.getautomatix.com/apt]("http://www.getautomatix/com/apt") edgy main
```Automatix is a bit flakey but people seem to swear by it.

---

### Post by Xoanan on 2007-10-22
I'm sorry, I misread your post.  I fixed that now;  Upgrade to  Fiesty has been completed with a few anomolies which I will post about later.  

Thanx

Xoanan

---

