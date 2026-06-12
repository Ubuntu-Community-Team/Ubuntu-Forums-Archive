---
title: "[SOLVED] Update Manager problem"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by tjololo on 2008-09-23
Hi
I have a problem with my package system that I can't figure out.
When i try to update my system I get this error:
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/source/Sources.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/source/Sources.gz)  302 Found
Some index files failed to download, they have been ignored, or old ones used instead.
I have tried searching the forum but can't find anything that fixes my problem.
--
tjololo

---

### Post by Elfy on 2008-09-23
That link ends up at a game site of some description - not too sure exactly as school french was a long time ago.

You have a problem with a source list - can you post the results of
```
sudo apt-get update
cat /etc/apt/sources.list
```

Please use [noparse]```

```[/noparse] tags around them.

---

### Post by tjololo on 2008-09-23
Output from sudo apt-get update:

```
Hit http://no.archive.ubuntu.com hardy-backports Release.gpg
Ign http://no.archive.ubuntu.com hardy-backports/main Translation-en_US                                                                                                         
Ign http://no.archive.ubuntu.com hardy-backports/restricted Translation-en_US                                                                                                   
Ign http://no.archive.ubuntu.com hardy-backports/universe Translation-en_US                                                                      
Ign http://no.archive.ubuntu.com hardy-backports/multiverse Translation-en_US                                                                    
Hit http://no.archive.ubuntu.com hardy-backports Release                                                                                         
Hit http://archive.canonical.com hardy Release.gpg                                         
Ign http://archive.canonical.com hardy/partner Translation-en_US                           
Hit http://no.archive.ubuntu.com hardy-backports/main Packages                             
Hit http://mirror.switch.ch hardy Release.gpg                        
Ign http://flomertens.keo.in edgy Release.gpg                                              
Hit http://no.archive.ubuntu.com hardy-backports/restricted Packages                       
Hit http://no.archive.ubuntu.com hardy-backports/universe Packages                         
Hit http://no.archive.ubuntu.com hardy-backports/multiverse Packages                       
Hit http://no.archive.ubuntu.com hardy-backports/main Sources                              
Hit http://archive.canonical.com hardy Release                                             
Hit http://no.archive.ubuntu.com hardy-backports/restricted Sources                        
Hit http://no.archive.ubuntu.com hardy-backports/universe Sources    
Hit http://no.archive.ubuntu.com hardy-backports/multiverse Sources  
Ign http://mirror.switch.ch hardy/main Translation-en_US             
Ign http://flomertens.keo.in edgy Release                            
Hit http://archive.canonical.com hardy/partner Packages
Ign http://mirror.switch.ch hardy/restricted Translation-en_US
Hit http://archive.canonical.com hardy/partner Sources
Ign http://flomertens.keo.in edgy/main-all Sources
Ign http://mirror.switch.ch hardy/universe Translation-en_US
Err http://flomertens.keo.in edgy/main-all Sources
  302 Found
Ign http://mirror.switch.ch hardy/multiverse Translation-en_US
Hit http://mirror.switch.ch hardy-updates Release.gpg
Ign http://mirror.switch.ch hardy-updates/main Translation-en_US
Ign http://mirror.switch.ch hardy-updates/restricted Translation-en_US
Ign http://mirror.switch.ch hardy-updates/universe Translation-en_US
Ign http://mirror.switch.ch hardy-updates/multiverse Translation-en_US
Hit http://mirror.switch.ch hardy-security Release.gpg
Ign http://mirror.switch.ch hardy-security/main Translation-en_US
Ign http://mirror.switch.ch hardy-security/restricted Translation-en_US
Ign http://mirror.switch.ch hardy-security/universe Translation-en_US
Ign http://mirror.switch.ch hardy-security/multiverse Translation-en_US
Hit http://mirror.switch.ch hardy Release
Hit http://mirror.switch.ch hardy-updates Release
Hit http://mirror.switch.ch hardy-security Release
Hit http://mirror.switch.ch hardy/main Packages
Hit http://mirror.switch.ch hardy/restricted Packages
Hit http://mirror.switch.ch hardy/main Sources
Hit http://mirror.switch.ch hardy/restricted Sources
Hit http://mirror.switch.ch hardy/universe Packages
Hit http://mirror.switch.ch hardy/universe Sources
Hit http://mirror.switch.ch hardy/multiverse Packages
Hit http://mirror.switch.ch hardy/multiverse Sources
Hit http://mirror.switch.ch hardy-updates/main Packages
Hit http://mirror.switch.ch hardy-updates/restricted Packages
Hit http://mirror.switch.ch hardy-updates/main Sources
Hit http://mirror.switch.ch hardy-updates/restricted Sources
Hit http://mirror.switch.ch hardy-updates/universe Packages
Hit http://mirror.switch.ch hardy-updates/universe Sources
Hit http://mirror.switch.ch hardy-updates/multiverse Packages
Hit http://mirror.switch.ch hardy-updates/multiverse Sources
Hit http://mirror.switch.ch hardy-security/main Packages
Hit http://mirror.switch.ch hardy-security/restricted Packages
Hit http://mirror.switch.ch hardy-security/main Sources
Hit http://mirror.switch.ch hardy-security/restricted Sources
Hit http://mirror.switch.ch hardy-security/universe Packages
Hit http://mirror.switch.ch hardy-security/universe Sources
Hit http://mirror.switch.ch hardy-security/multiverse Packages
Hit http://mirror.switch.ch hardy-security/multiverse Sources
W: Failed to fetch http://flomertens.keo.in/ubuntu/dists/edgy/main-all/source/Sources.gz  302 Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

my source.list:
```

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy multiverse
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security main restricted
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security main restricted
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security universe
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security universe
deb http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security multiverse
deb-src http://mirror.switch.ch/ftp/mirror/ubuntu/ hardy-security multiverse
#
#
deb-src http://flomertens.keo.in/ubuntu/ edgy main-all

```

---

### Post by Elfy on 2008-09-23
You have an old edgy reference at the end of your list - open the file to edit it and remove the last line

deb-src [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main-all

```
gksudo gedit /etc/apt/sources.list
```save and close then run the update again

```
sudo apt-get update
```

---

### Post by tjololo on 2008-09-23
aah! How could I miss that one:S
Thank you very much!

---

