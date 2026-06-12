---
title: "what's wrong with my repository?"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by SebbeJohan on 2007-05-28
Hi

I have a problem when I run sudo apt-get update:
```
sudo apt-get update
Err http://archive.ubuntu.com feisty Release.gpg                           
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com feisty-commercial Release.gpg             
  Could not resolve 'archive.canonical.com'
Err http://archive.ubuntu.com feisty/main Translation-en_US                
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com feisty-commercial/main Translation-en_US  
  Could not resolve 'archive.canonical.com'
Err http://archive.ubuntu.com feisty/restricted Translation-en_US          
  Could not resolve 'archive.ubuntu.com'
Ign http://archive.canonical.com feisty-commercial Release                 
Err http://archive.ubuntu.com feisty/universe Translation-en_US            
  Could not resolve 'archive.ubuntu.com'
Ign http://archive.canonical.com feisty-commercial/main Packages           
Err http://archive.ubuntu.com feisty/multiverse Translation-en_US          
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com feisty-commercial/main Packages           
  Could not resolve 'archive.canonical.com'
Get:1 http://archive.ubuntu.com feisty-updates Release.gpg [191B]          
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Get:2 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Get:3 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty-security Release
Hit http://archive.ubuntu.com feisty-backports Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/restricted Packages
Hit http://archive.ubuntu.com feisty/restricted Sources
Hit http://archive.ubuntu.com feisty/main Sources
Hit http://archive.ubuntu.com feisty/multiverse Sources
Hit http://archive.ubuntu.com feisty/universe Sources
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/main Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Packages
Hit http://archive.ubuntu.com feisty-updates/restricted Sources
Hit http://archive.ubuntu.com feisty-updates/main Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Sources
Hit http://archive.ubuntu.com feisty-updates/universe Sources
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-security/main Packages
Hit http://archive.ubuntu.com feisty-security/restricted Packages
Hit http://archive.ubuntu.com feisty-security/restricted Sources
Hit http://archive.ubuntu.com feisty-security/main Sources
Hit http://archive.ubuntu.com feisty-security/multiverse Sources
Hit http://archive.ubuntu.com feisty-security/universe Sources
Hit http://archive.ubuntu.com feisty-security/universe Packages
Hit http://archive.ubuntu.com feisty-security/multiverse Packages
Hit http://archive.ubuntu.com feisty-backports/main Packages
Hit http://archive.ubuntu.com feisty-backports/restricted Packages
Hit http://archive.ubuntu.com feisty-backports/universe Packages
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages
Fetched 3B in 3m21s (0B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/feisty-commercial/Release.gpg  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'
Failed to fetch http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/Packages.gz  Could not resolve 'archive.canonical.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
sebastian@sebastian-laptop:~$ 

```
here are my /etc/apt/sources.list
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ feisty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ feisty-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-security multiverse
# deb http://www.getautomatix.com/apt feisty main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
#AUTOMATIX REPOS END
```

What's wrong with my repository? any help much appreciated!

---

### Post by nekator on 2007-05-28
I can confirm this, cant launch software update using the GUI organe icon, tried sudo apt-get and got this crap=



Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Get:2 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
  302 Found
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:7 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  301 Moved Permanently
Get:9 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper Release
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Get:12 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:13 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [8412B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-updates/restricted Sources
Get:14 [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages [8925B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports/universe Sources
Get:15 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages [4452B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Get:16 [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages [4452B]
99% [16 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Waiting b zip2: (stdin) is not a bzip2 file.
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Fetched 28.9kB in 45s (637B/s)
Failed to fetch [http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-](http://www.beerorkid.com/automatix/apt/dists/dapper/main/binary-) i386/Packages.gz  302 Found
Failed to fetch [http://theli.free.fr/packages/dapper/./Packages.gz](http://theli.free.fr/packages/dapper/./Packages.gz)  301 Moved Pe rmanently
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Pa](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Pa) ckages.bz2  Sub-process bzip2 returned an error code (2)
Reading package lists... Error!
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_b inary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restric ted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/univers e Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_un iverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_b inary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restric ted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/univers e Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_un iverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_b inary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restric ted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/univers e Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_un iverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Pa ckages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_main_b inary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restric ted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/univers e Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_un iverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-updates_ multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packa ges)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i3 86_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packa ges)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i3 86_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packa ges)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i3 86_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages ( /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packa ges)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packag es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i3 86_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Pack ages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binar y-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_ma in_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restr icted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/unive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backport s_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multi verse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_ma in_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restr icted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/unive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backport s_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multi verse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_ma in_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restr icted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/unive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backport s_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multi verse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backports_ma in_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restr icted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/unive rse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backport s_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multi verse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper-backpo rts_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_ma in_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restr icted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-secur ity_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/unive rse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-securit y_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multi verse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-secur ity_multiverse_binary-i386_Packages)
E: Problem parsing dependency Depends
E: Error occurred while processing thekompany-support (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy _main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
nekator@nekator-desktop:~$

---

### Post by theaxis69 on 2007-05-28
I had a similar problem when running the Update Manager GUI.  I ran

sudo apt-get update

from the command line and it cleared the error message. Update Manager is now working again

---

### Post by SebbeJohan on 2007-05-28
well the weired thing for me is that update manager works perfectly, notifications popped up and I was able to go on with the upgrade ( I made a fresh new install 2 weeks ago). However, whenever I run sudo apt-get update from the terminal, it just seems to never find the its sources... The thing is that I have some installs I want to make and before anything else I need to update my system... Could anyone check my sources.list and tell me what's wrong (I've just remove automatix2 so I guess I don't need the source anymore) or just give me a link to the correct repository list (with everything enabled) please:KS?

---

