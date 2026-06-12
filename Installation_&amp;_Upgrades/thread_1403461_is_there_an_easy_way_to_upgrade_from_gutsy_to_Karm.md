---
title: "is there an easy way to upgrade from gutsy to Karmic Koala?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by ice60 on 2010-02-10
i broke my favourite computer lol so i'm using another that hasn't been updated from gutsy. is it easy to upgrade now to the lastest release?

---

### Post by OrangeCrate on 2010-02-10
The easiest way would be fresh install. Upgrading would involve moving through all of the versions from 7.10 to 9.10, one-at-a-time.

---

### Post by snowpine on 2010-02-10
Yes, it's easy. Boot with a Karmic Live CD and click Install. Oh yes, and back up your data first. :)

---

### Post by ice60 on 2010-02-10
what a nightmare! i hate having to setup a fresh install!!!! i did download the iso, but don't want to set it up. can someone do it for me? :D

---

### Post by snowpine on 2010-02-10
Really? Ubuntu is the most ready to go out of the box with the least setup required of any distro I've ever tried. You get a web browser, office suite, movie player, etc with zero setup required.

---

### Post by ice60 on 2010-02-10
> **snowpine said:**
> Really? Ubuntu is the most ready to go out of the box with the least setup required of any distro I've ever tried. You get a web browser, office suite, movie player, etc with zero setup required.
yes, it's good, but i make a lot of changes from the default install - lots of little scripts and hacks, programmes and setup changes. i'm probably just lazier than the average person lol

---

### Post by snowpine on 2010-02-10
Here's how to upgrade from gutsy. I will let you decide whether it's easier than a fresh install.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by ice60 on 2010-02-10
i am depressed! i don't think i'm cut out for fixed release distros :( i might have to go for a rolling release distro.

this is the computer i just broke, that was very old too -
[http://ubuntuforums.org/showthread.php?p=8783337#post8783337](http://ubuntuforums.org/showthread.php?p=8783337#post8783337)

---

### Post by wojox on 2010-02-10
arch is good. ;)

---

### Post by ice60 on 2010-02-10
> **wojox said:**
> arch is good. ;)
lol i wasn't going to mention arch. anyway, i decided to upgrade to the next release - Hardy Heron. i can slowly upgrade to the lastest release over time :)

---

### Post by ice60 on 2010-02-10
i haven't used ubuntu for a while and i'm not familiar with the sources, are these sources OK for an upgrade, is anything missing?
```
deb http://gb.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://gb.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://gb.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://gb.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse 
```
i just want the basic sources i think?

edit: i started the upgrade :D i hope it works!

---

### Post by slakkie on 2010-02-12
> **ice60 said:**
> i haven't used ubuntu for a while and i'm not familiar with the sources, are these sources OK for an upgrade, is anything missing?

i just want the basic sources i think?

edit: i started the upgrade :D i hope it works!

No, that is wrong, this is the correct way: [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

---

