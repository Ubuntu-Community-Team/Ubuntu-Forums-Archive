---
title: "F-port error install"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by tosbuntu on 2007-09-06
Hi, I'm new here, need some help for install F-prot.... " Error: cannot install 'libnet-perl". Thanks

---

### Post by bapoumba on 2007-09-06
libnet-perl is in the universe repository. You need to enable this repo:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by klas_katt on 2007-09-11
I cannot install the f-prot .deb with gdebi, it won't install libnet-perl. When I try to install libnet-perl with adept-manager (or synaptic), I get "BREAK (install) in the Requested column and when I preview changes 384 packages (from adept to xterm) will be removed. Including perl!

---

### Post by bapoumba on 2007-09-12
Could you please post your sources.list?
Open a terminal (> Accessories > Terminal), and paste the complete output to:
```
cat /etc/apt/sources.list
```

---

### Post by klas_katt on 2007-09-22
Sorry it took so long. I think I have the necessary repositories (just not multiverse) and libnet-perl is in there. Is this a free (as in freedom) software policy issue? I don't think libnet-perl would break for example xorg per se. 
```
klas_katt@commuter:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://se.archive.ubuntu.com/ubuntu/ feisty main restricted multiverse
#Addedby software-properties
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty restricted main universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted multiverse
#Addedby software-properties
deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#_______________________________________________________
deb http://se.archive.ubuntu.com/ubuntu/ feisty universe
#_______________________________________________________

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
deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted multiverse
#Addedby software-properties
deb-src http://security.ubuntu.com/ubuntu/ feisty-security restricted main universe
deb http://security.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main universe

########### ignore #########################
## adding this temporarily:
# sarge is older debian
# deb http://download.videolan.org/pub/videolan/debian/ sarge main
# deb-src http://download.videolan.org/pub/videolan/debian/ sarge main

#etch is stable
# deb http://www.debian-multimedia.org/ etch main
```

---

### Post by phantomcs on 2007-11-30
Hello, I'm new member, need some help for install F-prot in Ubuntu 7.04.... " Error: cannot install 'libnet-perl". Thanks..

---

