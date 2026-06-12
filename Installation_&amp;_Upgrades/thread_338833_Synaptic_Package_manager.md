---
title: "Synaptic Package manager"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2007-01-15
I check with my Synaptic Package manager , only shown 4450 packages Listed. It should be more than 15000+. Do you know why ?

---

### Post by bscbrit on 2007-01-15
What repos have you enabled? i.e. what is the content of your /etc/apt/sources.list ?

---

### Post by puneit on 2007-01-15
Visit this link
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by moonhk on 2007-01-15
it is second installation(four date ago). last time I can get 15000+ package. 
Which repo need to add ?

moonhk@hex:/mnt/backup$ cat /etc/apt/sources.list
#
# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
moonhk@hex:/mnt/backup$

---

### Post by bscbrit on 2007-01-16
Uncomment the repos  that are commented out (i.e. remove the '#' from the lines that contain deb .....)  You will have to do this as root so use the following command:

gksudo gedit /etc/apt/sources.list

Once you have uncommented the relevant lines, reload the database and you should have lots of packages available.

---

### Post by moonhk on 2007-01-17
It OK now.

moonhk@hex:/etc/apt$ cat *.list

# deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu-Server 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper main restricted multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) dapper-backports main restricted un iverse multiverse


deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security universe

moonhk@hex:/etc/apt$

---

