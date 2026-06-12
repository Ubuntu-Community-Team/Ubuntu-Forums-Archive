---
title: "System refusing to upgrade from 6.06LTS to 6.10"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by karaba on 2006-11-03
Hello,

I just tried to upgrade my system to 6.10 (I currently have a 6.06 installed from a liveCD a few months ago), following the "official" method:

gksu "update-manager -c"

The system asks me the password, downloads a bunch of files and then stops with an error message (two, in fact):

Failed to fetch cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/dists/dapper/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Any clues?

---

### Post by NetworkGuy on 2006-11-03
Can you show us what your /etc/apt/sources.list file looks like?

---

### Post by karaba on 2006-11-03
I suspect the first uncommented line is the culprit, but after reading several message exchanges like "I broke my ubuntu upgrading" and "yeah, that's because you manually edited your sources list file", I got really nervous about touching it... 
-------------------------------------------------------
#
# deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted


deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by towsonu2003 on 2006-11-03
I'd comment the line```
deb cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1)]/ dapper main restricted
```

I believe those comments are for customized installations. Like people adding repositories for 
* experimental packages (OpenOffice 2.0.4, wine and so on)
* xgl
* beryl
* other stuff

after uncommenting, ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop #to make sure you have the meta-package is installed, if you're using Ubuntu
``` and then follow the official way to upgrade to edgy. 

I would also google for known problems of upgrading dapper to edgy. you should know the problems (and solutions) bf you are done upgrading. 

and, **do backup** your files and assume that your system will be borked after the upgrade. it will probably not be borked, but being careful won't hurt you ;)

if you still aren't comfortable w. editing sources.list, insert your installation cd, mount it, and then go ahead (it wants to read the installation cd as a repository).

---

