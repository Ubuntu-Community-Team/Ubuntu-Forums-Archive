---
title: "Can't update after attempted Cloudera install"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by strangeone on 2012-11-21
Hi,

I am having real issues with my updating in 12.04, it seems to have started after I tried to install the Cloudera CDH, which failed, I think I have removed all the leftover code but can't be 100% sure.

I have spent some time in the forum and can't seem to fix my issue I have been through and apt-get clean and all to nothing.

Output

sudo apt-get update

> Get:1 [http://www.apache.org](http://www.apache.org) 10x InRelease [1,130 B]                            
Get:2 [http://dl.google.com](http://dl.google.com) stable InRelease [1,122 B]                          
Get:3 [http://www.apache.org](http://www.apache.org) 10x Release.gpg [1,134 B]                          
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [1,126 B]                        
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease [1,112 B]                     
Get:6 [http://www.apache.org](http://www.apache.org) 10x Release [1,126 B]                              
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease [1,154 B]                     
Ign [http://www.apache.org](http://www.apache.org) 10x Release                                          
E: GPG error: [http://www.apache.org](http://www.apache.org) 10x Release: The following signatures were invalid: NODATA 1 NODATA 2

The last error seems to vary, I am not sure why.

For 

cat /etc/apt/sources.list

> # deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

# MariaDB 5.5 repository list - created 2012-11-14 07:52 UTC
# [http://downloads.mariadb.org/mariadb/repositories/](http://downloads.mariadb.org/mariadb/repositories/)
deb [http://mirror2.hs-esslingen.de/mariadb/repo/5.5/ubuntu](http://mirror2.hs-esslingen.de/mariadb/repo/5.5/ubuntu) precise main
deb-src [http://mirror2.hs-esslingen.de/mariadb/repo/5.5/ubuntu](http://mirror2.hs-esslingen.de/mariadb/repo/5.5/ubuntu) precise main

deb [http://www.apache.org/dist/cassandra/debian](http://www.apache.org/dist/cassandra/debian) 10x main
deb-src [http://www.apache.org/dist/cassandra/debian](http://www.apache.org/dist/cassandra/debian) 10x main


I have tried commenting out the last 2 entries for MariaDB and Cassandra but it only picks something else.

I am really stuck so any advice would be greatly appreciated.

Many thanks

Rob

---

### Post by ibjsb4 on 2012-11-21
For GPG (badsig) errors

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gpg+error+badsig&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=gpg+error+badsig&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by strangeone on 2012-11-21
Thank you for coming back to me, I tried the following

[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

Option 1 - No change
Option 2 - aptitude not installed and I have no way of installing it as apt does not work.

Any other thoughts.

---

