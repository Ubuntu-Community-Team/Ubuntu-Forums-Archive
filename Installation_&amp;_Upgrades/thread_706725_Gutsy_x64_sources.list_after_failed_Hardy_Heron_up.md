---
title: "Gutsy x64 sources.list after failed Hardy Heron update"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by scamper_22 on 2008-02-24
Hi,

I tried to update my x64 install to hardy heron.  It wouldn't install..It seemed to stall at updating software channel after doing update-manager -d.  Anyways, I decided not to go any further as I saw other people had this problem too, but it did alter my sources list.  I changed all the heron to gutsy, but I'm still getting some failed sources.

I've search around and copied some sources.list, but all of them seem to have the same problem specifically with gutsy-security not being able to load.  Maybe it has something to do with my x64 install.  Could anyone please post that x64 gutsy sources.list or see what is wrong with mine.

Thanks

<code>
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free 



deb [http://download.tuxfamily.org/upure64/](http://download.tuxfamily.org/upure64/) feisty-upure64 main-amd64

#AUTOMATIX REPOS START

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gustsy-security main restricted universe multiverse

#ajunta IDE
deb [http://ppa.launchpad.net/robster/ubuntu](http://ppa.launchpad.net/robster/ubuntu) gutsy main restricted universe multiverse


</code>

These are the failed lines:
Err [http://security.ubuntu.com](http://security.ubuntu.com) gustsy-security/main Packages                   
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) gustsy-security/restricted Packages             
  404 Not Found

Err [http://security.ubuntu.com](http://security.ubuntu.com) gustsy-security/universe Packages             
  404 Not Found

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gustsy-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gustsy-security/main/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gustsy-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gustsy-security/restricted/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gustsy-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gustsy-security/universe/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gustsy-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/gustsy-security/multiverse/binary-amd64/Packages.gz)  404 Not Found

---

