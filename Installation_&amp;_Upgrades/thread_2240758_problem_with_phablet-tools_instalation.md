---
title: "problem with phablet-tools instalation"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by mrfsrf2 on 2014-08-22
hi,
spent all day trying to install phablet-tool on 12.04

here is summery of the process

android tools and dependencies all installed without problems

first i added thr ppa for phablet-tools
```
sudo add-apt-repository ppa:phablet-team/tools
```

than
```
sudo apt-get install phablet-tools
```

```
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 phablet-tools : Depends: click but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

cant install click either nor python3-clicks

if i trie to run 

```
sudo apt-get update
```
```
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise-updates Release.gpg
Hit http://archive.ubuntu.com precise-security Release.gpg
Hit http://ppa.launchpad.net precise Release.gpg                     
Hit http://ppa.launchpad.net precise Release.gpg                     
Hit http://archive.canonical.com precise Release.gpg
Hit http://ppa.launchpad.net precise Release   
Hit http://archive.ubuntu.com precise Release  
Hit http://archive.canonical.com precise Release
Hit http://archive.ubuntu.com precise-updates Release                 
Hit http://ppa.launchpad.net precise Release                          
Hit http://archive.ubuntu.com precise-security Release                
Hit http://ppa.launchpad.net precise/main Sources                     
Hit http://archive.ubuntu.com precise/main Sources                                          
Hit http://ppa.launchpad.net precise/main i386 Packages                                     
Ign http://ppa.launchpad.net precise/main TranslationIndex            
Hit http://archive.canonical.com precise/partner Sources                                    
Hit http://archive.ubuntu.com precise/restricted Sources                                    
Hit http://archive.ubuntu.com precise/universe Sources               
Hit http://archive.ubuntu.com precise/multiverse Sources             
Hit http://archive.ubuntu.com precise/main i386 Packages             
Hit http://archive.ubuntu.com precise/restricted i386 Packages       
Hit http://archive.ubuntu.com precise/universe i386 Packages         
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.canonical.com precise/partner i386 Packages
Ign http://archive.canonical.com precise/partner TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Hit http://archive.ubuntu.com precise-updates/main Sources
Hit http://archive.ubuntu.com precise-updates/restricted Sources
Hit http://archive.ubuntu.com precise-updates/universe Sources
Hit http://archive.ubuntu.com precise-updates/multiverse Sources     
Hit http://ppa.launchpad.net precise/main Sources                    
Hit http://ppa.launchpad.net precise/main i386 Packages              
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://archive.ubuntu.com precise-updates/main i386 Packages     
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages 
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex  
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://archive.ubuntu.com precise-security/main Sources          
Hit http://archive.ubuntu.com precise-security/restricted Sources    
Hit http://archive.ubuntu.com precise-security/universe Sources
Hit http://archive.ubuntu.com precise-security/multiverse Sources
Hit http://archive.ubuntu.com precise-security/main i386 Packages
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages
Hit http://archive.ubuntu.com precise-security/universe i386 Packages
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-security/main TranslationIndex 
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en            
Hit http://archive.ubuntu.com precise/multiverse Translation-en      
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en    
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en   
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US          
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


```

here is my /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner

deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse

```

and my /etc/apt/sources.d

```
arduino-ubuntu-team-ppa-karmic.list              lernid-devs-lernid-releases-karmic.list.distUpgrade
arduino-ubuntu-team-ppa-karmic.list.distUpgrade  lernid-devs-lernid-releases-karmic.list.save
arduino-ubuntu-team-ppa-karmic.list.save         phablet-team-tools-lucid.list
google-chrome.list                               phablet-team-tools-lucid.list.distUpgrade
google-chrome.list.distUpgrade                   phablet-team-tools-lucid.list.save
google-chrome.list.save                          phablet-team-tools-precise.list
jd-team-jdownloader-karmic.list                  phablet-team-tools-precise.list.save
jd-team-jdownloader-karmic.list.distUpgrade      prerequists-sources.list.save
jd-team-jdownloader-karmic.list.save             ubuntu-mozilla-daily-ppa-karmic.list
karmic-partner.list                              ubuntu-mozilla-daily-ppa-karmic.list.distUpgrade
karmic-partner.list.distUpgrade                  ubuntu-mozilla-daily-ppa-karmic.list.save
karmic-partner.list.save                         ubuntu-sdk-team-ppa-precise.list
lernid-devs-lernid-releases-karmic.list          ubuntu-sdk-team-ppa-precise.list.save

```

thanks for any help

---

### Post by mrfsrf2 on 2014-08-22
thing is i cant isntall click package which depenades on python3-click package which is broken

---

### Post by grahammechanical on 2014-08-22
You might get better results if you was running Ubuntu 14.04. I do not think that click packages can be installed on Desktop Ubuntu. Not even on Utoptic Unicorn. Not yet anyway. May be next year with 15.04 or 15.10. 

Have you installed the Ubuntu SDK as well?

[http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/](http://developer.ubuntu.com/start/ubuntu-for-devices/installing-ubuntu-for-devices/)

Regards.

---

