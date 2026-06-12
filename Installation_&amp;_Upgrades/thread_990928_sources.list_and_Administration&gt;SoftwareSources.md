---
title: "sources.list and Administration&gt;SoftwareSources&gt;Third party software dont match"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by joker77 on 2008-11-23
Hi,
I upgraded from ubuntu hardy to intrepid using Administration>Update Manager a couple of days after it was released. Things are working fine (except for the shutdown problem). Subsequent updates are also taking place ok. 
Presently my Third party Software sources (accessed using GUI as in title above) seems outdated. However my sources.list accessed using sudo gedit has the intrepid repos. 
How do I make the former match the latter? 

And one more unrelated question (once I get the above fixed) should all these 3rd party sources be selected or unselected if I want regular updates from them?

My 3rd party list consists of: (copied by hand)

CD rom with ubuntu 8.04 'hardy heron'
Unsupported updates
http:// archive.canonical.com/ubuntu hardy partner
http:// archive.canonical.com/ubuntu hardy partner (Source Code)
[http://mirrors.ibiblio.org/pub/mirrors/CRAN/bin/linux/ubuntu](http://mirrors.ibiblio.org/pub/mirrors/CRAN/bin/linux/ubuntu) hardy/
[http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy) free non-free
[http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy) free non-free (Source Code)

While my source.list is (pasted here)

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid main restricted
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates main restricted
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid universe
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid universe
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates universe
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid multiverse
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid multiverse
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates multiverse
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security main restricted
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security main restricted
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security universe
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security universe
deb [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security multiverse
deb-src [ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/](ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/) intrepid-security multiverse

##Source for R files- currently using intrepid repository
# deb [http://mirrors.ibiblio.org/pub/mirrors/CRAN/bin/linux/ubuntu](http://mirrors.ibiblio.org/pub/mirrors/CRAN/bin/linux/ubuntu) hardy/

##Intrepid medibuntu repository
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) intrepid universe multiverse

Umm... sorry if this is an unnecessarily bulky mail. Your advice would be highly appreciated. Thanks!

---

### Post by Pumalite on 2008-11-23
Third parties including Medibuntu and it's folder should be removed BEFORE attempting an upgrade

---

