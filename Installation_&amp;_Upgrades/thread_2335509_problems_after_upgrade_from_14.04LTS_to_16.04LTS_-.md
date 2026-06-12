---
title: "problems after upgrade from 14.04LTS to 16.04LTS - software, uppgrade language suppor"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by martin-bermann on 2016-08-29
Hi!
I have a problem with my 16.04 installation. 
sudo apt update
[sudo] Passwort für martin: 
E: Malformed entry 55 in list file /etc/apt/sources.list (URI parse)
E: The list of the source cannot be read (Die Liste der Quellen konnte nicht gelesen werden.)

I have no idea how to solve that. I think the best would be to make a new installation or changing some files, but I do not have such a knowledge to solve this. Is there someone who can help me?
I think with this problem I even be not able to get automatically updates.

The language support is also not working. I cannot change the language from DE to EN for example without crash.

THX for some support
Martin

---

### Post by howefield on 2016-08-29
Please post the output of 

```
cat /etc/apt/sources.list
```

It will be a simple matter of changing the file so that it works.

---

### Post by martin-bermann on 2016-08-29
```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

# deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # Bei Aktualisierung zu xenial deaktiviert
# deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb http//www.mediahuman.com/packages/ubuntu trusty main
# deb-src http//www.mediahuman.com/packages/ubuntu trusty main
```

---

### Post by howefield on 2016-08-29
OK, seeing as you are already in terminal, use...

```
sudo apt edit-sources
```

and select nano, option 2.

Cursor down to the second from last line that says *"deb http//www.mediahuman.com/packages/ubuntu trusty main"* and put a # sign at the beginning.

Ctrl + O keys to save the file, enter and Ctrl + X keys to exit.

You should then be able to do a 

```
sudo apt update
```

The question then is whether or not you still need/want the mediahuman lines and whether it has a xenial repository or not.

---

### Post by grahammechanical on 2016-08-29
This is not a URL to a repository

```
deb http//www.mediahuman.com/packages/ubuntu trusty main
```

This is a URL to a repository

```
deb http://www.mediahuman.com/packages/ubuntu trusty main
```

The colon ( : ) makes the difference.

Regards

---

### Post by martin-bermann on 2016-08-29
howefield! I don't know what to say...thank you so much running again :-) many thanks

---

### Post by howefield on 2016-08-29
> **martin-bermann said:**
> howefield! I don't know what to say...thank you so much running again :-) many thanks

You are very welcome.

As grahammechanical pointed out above, you can enable the line again by removing the # sign and inserting the missing colon. However, having looked at the software included in that site, I'd suggest there are native packages within the Ubuntu repositories that would most likely do what you need. 

There is also the fact that it is marked for Trusty, and may not work in 16.04.

---

