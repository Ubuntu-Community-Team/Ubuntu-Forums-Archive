---
title: "Sys-Admin-Software Sources help needed!"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by hodad on 2007-11-21
I'm trying to add repositories per the instructions on the Ubuntu Support website, but the instructions are incomplete.

After clicking "Add", and entring the URL, the example shows 'deb <URL> gutsy restricted" or some such example.   

I encountered two problems:
I can get the URL from the proper website, but when I enter it, and tack on "deb" (whatever that means) to the front, what do I add to the back end of the line.  I can't just leave it blank, or it won't let me enter it.  Do I just type 'gutsy restricted' on each repository listing?  

Anyway, I tried that, in order to make my line look more like the example listed on the "add repository"  instructions.  However, when I save the new repository listing, and try to use it to retrieve the desired software, there is a message that it can't access the repository.

Can anyone provide a more complete explanation of how to add repositories than is listed under Ubuntu Support on the Ubuntu website? I've been trolling the fora, but can't find what I'm looking for.

Thanks!

Thanks

---

### Post by bapoumba on 2007-11-22
Please post your source.list. Open a terminal (> Accessories > Terminal) and paste the output to:
```
cat /etc/apt/sources.list
```
Which repositories do you want to add?

---

### Post by hodad on 2007-11-23
Not sure exactly what locations to put in as the source address; is the home address of the entity providing the downloads sufficient, or do you need an exact URL of the file itself?

Anyway, here's  the listing:

el@ubuntu:~$ cat /etc/apt/sources.list
## Ubuntu 7.10 Software Repositories

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'commercial' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy commercial

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

## System76 Repository.  This software repository contains drivers and
## updates specifically for your computer
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./


Thanks!

---

### Post by bapoumba on 2007-11-24
My own source.list is basically the same as yours, except the gutsy-proposed, which I would not keep (these are for testing packages, and likely to break things), and the System76 repos.
Which repos do you want to add or packages to install?

---

