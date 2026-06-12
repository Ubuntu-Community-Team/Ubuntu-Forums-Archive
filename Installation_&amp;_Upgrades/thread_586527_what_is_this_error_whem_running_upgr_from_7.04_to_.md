---
title: "what is this error whem running upgr from 7.04 to 7.10?"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by air3d44 on 2007-10-22
Hi,

At the begining when running upgrade after couple fetching I am getting this errors:

Failed to fetch [http://mirror.noreply.org/pub/tor/dists/feisty/Release.gpg](http://mirror.noreply.org/pub/tor/dists/feisty/Release.gpg) Bad header line
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/feisty/main/i18n/Translation-en_US.bz2](http://mirror.noreply.org/pub/tor/dists/feisty/main/i18n/Translation-en_US.bz2) Bad header line
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  universedeb/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/feisty/main/binary-i386/Packages.gz](http://mirror.noreply.org/pub/tor/dists/feisty/main/binary-i386/Packages.gz) Bad header line
Failed to fetch [http://mirror.noreply.org/pub/tor/dists/feisty/main/source/Sources.gz](http://mirror.noreply.org/pub/tor/dists/feisty/main/source/Sources.gz) Bad header line


Any Idea?

Thanks a lot.

Carl

---

### Post by Sef on 2007-10-22
Did you install anything to your source list, e.g. automatix?

Copy and paste your source list here.

Applications > Accessories > Terminal

then type or copy and paste this command:

```
cat /etc/apt/sources.list
```

then copy and paste your source list here.

---

### Post by air3d44 on 2007-10-22
Yes i had automatix2 but I uninstaled already.

My source list:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security main restricted multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-security universedeb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) feisty main
#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security universe
#AUTOMATIX REPOS END



Thanks for help.

Carl

---

### Post by air3d44 on 2007-10-22
Any Idea?

C

---

### Post by Seisen on 2007-10-22
You need to comment out these lines

```

deb http://mirror.noreply.org/pub/tor feisty main
deb-src http://mirror.noreply.org/pub/tor feisty main
deb http://www.getautomatix.com/apt feisty main
``` just add a "#" in front of each line then run ```
sudo apt-get update
``` then try upgrading to gusty and it should give you any problems.

---

### Post by air3d44 on 2007-10-22
Thanks Seisen...it helped with those 3 but I am still getting this one:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release) Unable to find expected entry  universedeb/binary-i386/Packages in Meta-index file (malformed Release file?)

Thanks for help.

C

---

### Post by air3d44 on 2007-10-22
and when running sudo apt-get update from terminal I am getting this error:


Fetched 7B in 7s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release](http://us.archive.ubuntu.com/ubuntu/dists/feisty-security/Release)  Unable to find expected entry  universedeb/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Thanks.

C

---

