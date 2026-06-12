---
title: "Synaptic not seeing repos"
date: 2010-02-06
forum: Installation &amp; Upgrades
---

### Post by Lostin60's on 2010-02-06
I have 2 new repos that are listed in my sources.list file.  They are also visible in System/Administration/Software Sources/Other Software.  However, they are not visible under the  Origins tab in Synaptic.  Why would this be?  And how would I download from them if Synaptic doesn't see them?

---

### Post by mushwars on 2010-02-06
you need to do this

```
sudo apt-get update
```


then it will "see" your repo's

cheers

---

### Post by Lostin60's on 2010-02-06
> **mushwars said:**
> you need to do this

```
sudo apt-get update
```


then it will "see" your repo's

cheers

mushwars Already tried that. apt-get update only updates repos it sees.  It doesn't seem to see my new ones...sigh

---

### Post by mushwars on 2010-02-06
actually that is not true, I could go into /etc/apt/soruces.list and add joe blows repoisitory then apt-get update and then apt-get install joeblowsprogram.

There is something else wrong can you paste your /etc/apt/sources.list ?

---

### Post by Lostin60's on 2010-02-06
> **mushwars said:**
> actually that is not true, I could go into /etc/apt/soruces.list and add joe blows repoisitory then apt-get update and then apt-get install joeblowsprogram.

There is something else wrong can you paste your /etc/apt/sources.list ?


mushwars  Here's the file. And as I said you can see lines 48 & 49 in System/Administration/Software Sources/Other Software.  Makes no sense to me??

deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb file:/usr/local/mydebs ./
deb [http://ftp.us.debian.org/debian](http://ftp.us.debian.org/debian) sid  main
deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) sid  main

---

### Post by mushwars on 2010-02-06
oh yea, I forgot to ask you what packages are you trying to install, that way I know which repos you need in that sources file. Otherwise I dont know if you have what you need in there or not >_<

---

### Post by Lostin60's on 2010-02-06
> **mushwars said:**
> oh yea, I forgot to ask you what packages are you trying to install, that way I know which repos you need in that sources file. Otherwise I dont know if you have what you need in there or not >_<

Well for starters, python-gobject-dev_2.20.0-1_all.deb. Discovered I needed the gpg keys..getting them now.

---

### Post by mushwars on 2010-02-06
> **Lostin60's said:**
> Well for starters, python-gobject-dev_2.20.0-1_all.deb. Discovered I needed the gpg keys..getting them now.

yea that package requires
deb [http://*ftp.de.debian.org/debian](http://*ftp.de.debian.org/debian)* sid main 

which you already have. So, right you need to get the key.

---

### Post by Lostin60's on 2010-02-06
> **mushwars said:**
> yea that package requires
deb [http://*ftp.de.debian.org/debian](http://*ftp.de.debian.org/debian)* sid main 

which you already have. So, right you need to get the key.

Which is seemingly easier said than done...heheh

---

