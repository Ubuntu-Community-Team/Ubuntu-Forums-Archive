---
title: "how to install request tracker on ubuntu 12.04-server"
date: 2012-12-26
forum: Installation &amp; Upgrades
---

### Post by teejabar on 2012-12-26
HI,please i want to install request tracker, so i decided to do a fresh installation of ubuntu12.04lts server. I downloaded ubuntu 12. 04.1-server i386.iso ,i did checksum before burning to a DVD,after which Iinstalled. After the installation, i wanted to proceed to first see if am updated,so i typed sudo apt-get inthe terminal,but i got a long list of errors.The last line of the error is 
E: Some index files failed to download. They have been ignored, or old ones used instead.

What should i do.

---

### Post by Kirk Schnable on 2012-12-26
Could you copy/paste or screenshot the entire error?  It will definitely be helpful in our resolving your problems. 

Could you also give me the output of these commands for our reference while troubleshooting?

```
ls /etc/apt/sources.list.d
```

```
cat /etc/apt/sources.list
```

Thanks

---

### Post by teejabar on 2012-12-27
when i type ls /etc/apt/sources.list.d, i get
adilson-experimental-maverick.list  adilson-experimental-maverick.list.save

---

### Post by teejabar on 2012-12-27
when i type cat /etc/apt/sources.list, i got

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb mirror://mirrors.ubuntu.com/mirrors.txt maverick main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt maverick-updates main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt maverick-backports main restricted universe multiverse
deb mirror://mirrors.ubuntu.com/mirrors.txt maverick-security main restricted universe multiverse

deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick main restricted
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates main restricted
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick universe
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick universe
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates universe
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick multiverse
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick multiverse
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates multiverse
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security main restricted
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security main restricted
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security universe
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security universe
deb [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security multiverse
deb-src [http://ftp.sh.cvut.cz/MIRRORS/ubuntu/](http://ftp.sh.cvut.cz/MIRRORS/ubuntu/) maverick-security multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main

---

### Post by Cheesemill on 2012-12-27
You've installed 10.10, not 12.04.

10.10 reached end of life 8 months ago and as such doesn't receive any bug fixes or security updates any more.

This is the reason you can't download and install any software, the repositories have been taken off line.

---

