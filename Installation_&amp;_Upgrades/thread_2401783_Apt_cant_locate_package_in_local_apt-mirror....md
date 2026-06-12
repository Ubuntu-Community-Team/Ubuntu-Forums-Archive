---
title: "Apt cant locate package in local apt-mirror..."
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by jagdtigger on 2018-09-22
Greetings :) .

I have troubles with a fresh Kubuntu install. I have a local apt-mirror with the following config:
```
#Ubuntu bionic
###### Ubuntu Main Repos
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted universe multiverse
deb-i386 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) bionic main restricted universe multiverse


###### Ubuntu Update Repos
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-security main restricted universe multiverse
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-updates main restricted universe multiverse
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-proposed main restricted universe multiverse
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse


deb-i386 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse
deb-i386 [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-security main restricted universe multiverse
deb-i386 [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-updates main restricted universe multiverse
deb-i386 [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-proposed main restricted universe multiverse
deb-i386 [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse


###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner
deb-i386 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic partner


###### Ubuntu Extras Repo
#deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) bionic main
```

The local sourcers.list:
```
# deb cdrom:[Ubuntu-MATE 17.10 _Artful Aardvark_ - Release amd64 (20171018)]/ artful main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic main restricted
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic-updates main restricted
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic universe
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful universe
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic-updates universe
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic multiverse
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful multiverse
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic-updates multiverse
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://10.125.210.23/apt-mirror/ubuntu/](http://10.125.210.23/apt-mirror/ubuntu/) bionic-backports main restricted universe multiverse
# deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) artful-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) artful partner

deb [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu-security](http://security.ubuntu.com/ubuntu-security) artful-security main restricted
deb [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security universe
# deb-src [http://security.ubuntu.com/ubuntu-security](http://security.ubuntu.com/ubuntu-security) artful-security universe
deb [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu-security](http://security.ubuntu.com/ubuntu-security) artful-security multiverse


deb [http://10.125.210.23/apt-mirror/wine-builds/ubuntu/](http://10.125.210.23/apt-mirror/wine-builds/ubuntu/) artful main
# deb [http://10.125.210.23/apt-mirror/wine-builds/ubuntu/](http://10.125.210.23/apt-mirror/wine-builds/ubuntu/) bionic main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) artful main
deb [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic contrib

```

apt-get update output:
```
root@patakija-MS-7821:/home/patakija# apt-get update
Get:1 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic InRelease [242 kB]
Get:2 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates InRelease [88,7 kB]                         
Get:3 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-backports InRelease [74,6 kB]                                    
Get:4 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security InRelease [83,2 kB]                                     
Get:5 [http://10.125.210.23/apt-mirror/wine-builds/ubuntu](http://10.125.210.23/apt-mirror/wine-builds/ubuntu) artful InRelease [4.701 B]                                  
Get:6 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main amd64 Packages [1.019 kB]                                   
Get:7 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main i386 Packages [1.007 kB]                         
Get:8 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main Translation-en [516 kB]                          
Get:9 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main amd64 DEP-11 Metadata [477 kB]                   
Get:10 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 48x48 Icons [118 kB]                     
Get:11 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64 Icons [245 kB]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]                     
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:20 [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic InRelease [4.429 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Err:5 [http://10.125.210.23/apt-mirror/wine-builds/ubuntu](http://10.125.210.23/apt-mirror/wine-builds/ubuntu) artful InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 818A435C5FCBF54A
Err:20 [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Ign:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons
Ign:77 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/universe DEP-11 64x64@2 Icons
Ign:78 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/multiverse DEP-11 64x64@2 Icons
Ign:79 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/main DEP-11 64x64@2 Icons
Ign:80 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/universe DEP-11 64x64@2 Icons
Ign:81 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/multiverse DEP-11 128x128 Icons
Ign:82 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-backports/universe DEP-11 128x128 Icons
Get:83 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/main DEP-11 128x128 Icons [29 B]
Get:83 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/main DEP-11 128x128 Icons [29 B]
Ign:83 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/main DEP-11 128x128 Icons
Ign:84 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/universe DEP-11 64x64@2 Icons
Get:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons [29 B]
Ign:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons
Ign:77 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/universe DEP-11 64x64@2 Icons
Ign:78 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/multiverse DEP-11 64x64@2 Icons
Ign:79 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/main DEP-11 64x64@2 Icons
Ign:80 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/universe DEP-11 64x64@2 Icons
Ign:84 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/universe DEP-11 64x64@2 Icons
Err:12 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/main DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Ign:77 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/universe DEP-11 64x64@2 Icons
Ign:78 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic/multiverse DEP-11 64x64@2 Icons
Err:79 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/main DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Ign:80 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-updates/universe DEP-11 64x64@2 Icons
Err:84 [http://10.125.210.23/apt-mirror/ubuntu](http://10.125.210.23/apt-mirror/ubuntu) bionic-security/universe DEP-11 64x64@2 Icons
  404  Not Found [IP: 10.125.210.23 80]
Reading package lists... Done      
W: GPG error: [http://10.125.210.23/apt-mirror/wine-builds/ubuntu](http://10.125.210.23/apt-mirror/wine-builds/ubuntu) artful InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 818A435C5FCBF54A
E: The repository 'http://10.125.210.23/apt-mirror/wine-builds/ubuntu artful InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
E: The repository 'https://download.virtualbox.org/virtualbox/debian bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```
(Ignore the gpg error, its a file from the previous install so it has some repos that does not have their keys installed yet.)

apt-get install htop(i tried several others too but same result):
```

root@patakija-MS-7821:/home/patakija# apt-get install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package htop

```

If i switch back to the original repos i can install software, only the local one has problems. When i run apt-mirror manually i do not get any errors. Where should i start?

Thanks in advance for the help :) .

---

### Post by jagdtigger on 2018-09-23
Last ditch effort i deleted the repos and re-downloaded the whole thing. Now apt-get says no release file:
> E: The repository 'http://10.125.210.23/apt-mirror/ubuntu bionic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://10.125.210.23/apt-mirror/ubuntu bionic-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://10.125.210.23/apt-mirror/ubuntu bionic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


---

### Post by timothylegg on 2018-09-23
If you get this figured out, I want to know.  I created a nearly identical post on this yesterday.  Nobody saw it so I'm bumping it.

---

### Post by jagdtigger on 2018-09-24
It most be something with the web server. Mounted the repos locally and pointed apt to those folders. Now it gets everything without nagging about release files....

/EDIT
Okay, so it updates without the previous issues, but i still cant install anything:
```
root@patakija-MS-7821:/home/patakija# apt-get update      
Get:1 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:1 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic InRelease [242 kB]
Get:2 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]
Get:3 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]
Get:4 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
Get:5 file:/mnt/apt-mirror/mirror/dl.winehq.org/wine-builds/ubuntu artful InRelease [4.701 B]
Get:2 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]
Get:3 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]
Get:4 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security InRelease [83,2 kB]
Get:5 file:/mnt/apt-mirror/mirror/dl.winehq.org/wine-builds/ubuntu artful InRelease [4.701 B]
Get:6 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1.019 kB]
Ign:6 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 Packages
Get:7 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1.007 kB]
Ign:7 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main i386 Packages
Get:8 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]
Ign:8 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main Translation-en
Get:9 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Ign:9 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata
Get:10 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Ign:10 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons
Get:11 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]
Ign:11 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons
Get:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons [29 B]
Ign:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons
Get:13 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 128x128 Icons [602 kB]
Ign:13 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 128x128 Icons
Get:14 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [9.184 B]
Ign:14 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages
Get:15 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages [9.156 B]
Ign:15 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages
Get:16 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted Translation-en [3.584 B]
Ign:16 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted Translation-en
Get:17 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8.531 kB]
Ign:17 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe i386 Packages
Get:18 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8.570 kB]
Ign:18 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
Get:19 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4.941 kB]
Ign:19 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe Translation-en
Get:20 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [3.287 kB]
Ign:20 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata
Get:21 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons [2.151 kB]
Ign:21 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons
Get:22 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8.420 kB]
Ign:22 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons
Get:23 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons [29 B]
Ign:23 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons
Get:24 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 128x128 Icons [16,6 MB]
Ign:24 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 128x128 Icons
Get:25 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages [144 kB]
Ign:25 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages
Get:26 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
Ign:26 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages
Get:27 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
Ign:27 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en
Get:28 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49,7 kB]
Ign:28 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata
Get:29 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 48x48 Icons [8.931 B]
Ign:29 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 48x48 Icons
Get:30 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]
Ign:30 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons
Get:31 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64@2 Icons [29 B]
Ign:31 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64@2 Icons
Get:32 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 128x128 Icons [472 kB]
Ign:32 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 128x128 Icons
Get:6 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 Packages [1.019 kB]
Get:7 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main i386 Packages [1.007 kB]
Get:8 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main Translation-en [516 kB]                       
Get:9 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]                    
Get:10 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 48x48 Icons [118 kB]
Get:11 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64 Icons [245 kB]                    
Get:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons [29 B]                    
Ign:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons
Get:13 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 128x128 Icons [602 kB]
Get:14 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages [9.184 B]                   
Get:15 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted i386 Packages [9.156 B]                
Get:16 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/restricted Translation-en [3.584 B]               
Get:17 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe i386 Packages [8.531 kB]
Get:18 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages [8.570 kB]                       
Get:19 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe Translation-en [4.941 kB]                         
Get:20 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe amd64 DEP-11 Metadata [3.287 kB]                        
Get:21 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 48x48 Icons [2.151 kB]                             
Get:22 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64 Icons [8.420 kB]
Get:23 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons [29 B]                   
Ign:23 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 64x64@2 Icons                
Get:24 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/universe DEP-11 128x128 Icons [16,6 MB]      
Get:25 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages [144 kB]
Get:26 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages [151 kB]
Get:27 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse Translation-en [108 kB]
Get:28 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse amd64 DEP-11 Metadata [49,7 kB]  
Get:29 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 48x48 Icons [8.931 B]        
Get:30 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64 Icons [225 kB]
Get:31 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64@2 Icons [29 B]   
Ign:31 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 64x64@2 Icons  
Get:32 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/multiverse DEP-11 128x128 Icons [472 kB]
Get:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons [1.024 B]
Err:12 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic/main DEP-11 64x64@2 Icons        
  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar (2: No such file or directory)
Get:33 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [351 kB]
Ign:33 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages
Get:34 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [315 kB]
Ign:34 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages
Get:35 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [132 kB]
Ign:35 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en       
Get:36 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [139 kB]
Ign:36 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata
Get:37 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [31,4 kB]
Ign:37 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons
Get:38 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [56,9 kB]
Ign:38 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons
Get:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons [29 B]
Ign:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons
Get:40 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [144 kB]
Ign:40 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons
Get:41 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [206 kB]
Ign:41 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages
Get:42 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [206 kB]
Ign:42 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages
Get:43 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [98,0 kB]
Ign:43 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en   
Get:44 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [166 kB]
Ign:44 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata
Get:45 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [170 kB]
Ign:45 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons
Get:46 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [279 kB]
Ign:46 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons
Get:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons [29 B]
Ign:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons
Get:48 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [693 kB]
Ign:48 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons
Get:49 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [4.180 B]
Ign:49 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages
Get:50 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [4.336 B]
Ign:50 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages
Get:51 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en [2.740 B]
Ign:51 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en 
Get:52 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.464 B]
Ign:52 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata
Get:53 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Ign:53 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 48x48 Icons
Get:54 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64 Icons [2.638 B]
Ign:54 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64 Icons
Get:55 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64@2 Icons [29 B]
Ign:55 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64@2 Icons
Get:56 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 128x128 Icons [29 B]
Ign:56 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 128x128 Icons
Get:57 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [2.852 B]
Ign:57 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages
Get:58 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages [2.848 B]
Ign:58 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages
Get:59 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en [1.200 B]
Ign:59 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en
Get:60 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5.100 B]
Ign:60 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata
Get:61 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]
Ign:61 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 48x48 Icons
Get:62 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1.789 B]
Ign:62 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64 Icons
Get:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons [29 B]
Ign:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons
Get:64 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 128x128 Icons [29 B]
Ign:64 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 128x128 Icons
Get:65 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [168 kB]
Ign:65 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
Get:66 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main i386 Packages [134 kB]
Ign:66 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main i386 Packages   
Get:67 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main Translation-en [63,6 kB]
Ign:67 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main Translation-en        
Get:68 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Ign:68 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata
Get:69 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]
Ign:69 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons 
Get:70 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B]
Ign:70 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons 
Get:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons [29 B]
Ign:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons 
Get:72 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 128x128 Icons [29 B]
Ign:72 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 128x128 Icons 
Get:73 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [66,8 kB]
Ign:73 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages
Get:74 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [66,7 kB]
Ign:74 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe i386 Packages
Get:75 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe Translation-en [39,3 kB]
Ign:75 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe Translation-en    
Get:76 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [6.828 B]
Ign:76 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata
Get:77 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9.090 B]
Ign:77 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons
Get:78 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [11,3 kB]
Ign:78 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons
Get:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons [29 B]
Ign:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons
Get:80 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons [31,6 kB]
Ign:80 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons
Get:81 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1.444 B]
Ign:81 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages
Get:82 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages [1.608 B]
Ign:82 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages
Get:83 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [996 B]
Ign:83 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse Translation-en  
Get:33 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [351 kB]
Get:34 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [315 kB]   
Get:35 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [132 kB]  
Get:36 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [139 kB] 
Get:37 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [31,4 kB]
Get:38 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [56,9 kB]
Get:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons [29 B]
Ign:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons
Get:40 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 128x128 Icons [144 kB]
Get:41 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [206 kB]
Get:42 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [206 kB]
Get:43 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe Translation-en [98,0 kB]
Get:44 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [166 kB]
Get:45 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [170 kB]  
Get:46 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [279 kB]
Get:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons [29 B]
Ign:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons
Get:48 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 128x128 Icons [693 kB]
Get:49 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 Packages [4.180 B]
Get:50 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse i386 Packages [4.336 B]
Get:51 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse Translation-en [2.740 B]
Get:52 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2.464 B]
Get:53 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 48x48 Icons [29 B]
Get:54 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64 Icons [2.638 B]
Get:55 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64@2 Icons [29 B]
Ign:55 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 64x64@2 Icons
Get:56 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/multiverse DEP-11 128x128 Icons [29 B]
Get:57 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 Packages [2.852 B]
Get:58 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe i386 Packages [2.848 B]
Get:59 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe Translation-en [1.200 B]
Get:60 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5.100 B]
Get:61 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 48x48 Icons [29 B]
Get:62 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64 Icons [1.789 B]
Get:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons [29 B]
Ign:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons
Get:64 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 128x128 Icons [29 B]
Get:65 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [168 kB]     
Get:66 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main i386 Packages [134 kB]   
Get:67 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main Translation-en [63,6 kB] 
Get:68 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]   
Get:69 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [29 B]
Get:70 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [29 B] 
Get:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons [29 B]
Ign:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons
Get:72 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 128x128 Icons [29 B]
Get:73 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [66,8 kB]
Get:74 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [66,7 kB]
Get:75 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe Translation-en [39,3 kB]
Get:76 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [6.828 B]
Get:77 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [9.090 B]  
Get:78 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [11,3 kB]
Get:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons [29 B]
Ign:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons
Get:80 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 128x128 Icons [31,6 kB]
Get:81 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse amd64 Packages [1.444 B] 
Get:82 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse i386 Packages [1.608 B]
Get:83 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/multiverse Translation-en [996 B]
Get:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons [1.024 B]
Err:39 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64@2 Icons
  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/dep11/icons-64x64@2.tar (2: No such file or directory)
Get:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons [1.024 B]
Ign:47 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64@2 Icons
Get:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons [1.024 B]
Err:63 file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu bionic-backports/universe DEP-11 64x64@2 Icons
  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/dep11/icons-64x64@2.tar (2: No such file or directory)
Get:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons [1.024 B]
Err:71 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64@2 Icons
  File not found - /mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu/dists/bionic-security/main/dep11/icons-64x64@2.tar (2: No such file or directory)
Get:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons [1.024 B]
Ign:79 file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64@2 Icons
Hit:84 [https://download.virtualbox.org/virtualbox/debian](https://download.virtualbox.org/virtualbox/debian) bionic InRelease                              
Reading package lists... Done 
N: Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'https://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386'
E: Failed to fetch file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic/main/dep11/icons-64x64@2.tar (2: No such file or directory)
E: Failed to fetch file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/dep11/icons-64x64@2.tar  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/dep11/icons-64x64@2.tar (2: No such file or directory)
E: Failed to fetch file:/mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/dep11/icons-64x64@2.tar  File not found - /mnt/apt-mirror/mirror/hu.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/dep11/icons-64x64@2.tar (2: No such file or directory)
E: Failed to fetch file:/mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu/dists/bionic-security/main/dep11/icons-64x64@2.tar  File not found - /mnt/apt-mirror/mirror/security.ubuntu.com/ubuntu/dists/bionic-security/main/dep11/icons-64x64@2.tar (2: No such file or directory)
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@patakija-MS-7821:/home/patakija# sudo apt-get install gparted htop iotop nmap kicad freecad librecad octave mc synaptic  -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gparted
E: Unable to locate package iotop
E: Unable to locate package nmap
E: Unable to locate package kicad
E: Unable to locate package freecad
E: Unable to locate package librecad
E: Unable to locate package octave
root@patakija-MS-7821:/home/patakija# 
```

---

### Post by jagdtigger on 2018-09-26
This was a very looong search but finally hit the solution:
[https://askubuntu.com/questions/771547/ubuntu-16-04-apt-get-update-doesnt-work-with-local-repository](https://askubuntu.com/questions/771547/ubuntu-16-04-apt-get-update-doesnt-work-with-local-repository)

---

### Post by timothylegg on 2018-09-28
Yeah, they aren't much help here...  UbuntuForums is pretty dead, probably should try a different site.  Do you have suggestions where people are moving to?  Search engines are woefully slow at following forum growth.

I moved the 50appstream file away from /etc/ but that didn't change anything.  apt-get still can't find packages, none of them.  What's wild is that that if I try a package that's already installed, it is able to determine that I have the most current version...

---

### Post by QIII on 2018-09-28
If there is no help to be had on the UF, I might as well close the thread.

Cheers!

---

