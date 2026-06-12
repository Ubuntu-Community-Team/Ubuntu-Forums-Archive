---
title: "Unable to upgrade Ubuntu 16.04.5 to 18.04.1"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by tehmeh2 on 2018-08-21
Hello,

I have a problem when upgrading Ubuntu 16.04.5 to Ubuntu 18.04.1. The upgrade is simply aborted without error messages and I am no really sure where to start looking.
The output that I get when upgrading is:
```
$ do-release-upgrade 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                                               
Get:2 Upgrade tool [1.258 kB]                                                                      
Fetched 1.258 kB in 0s (0 B/s)                                                                     
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
extracting 'bionic.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit http://repo.steampowered.com/steam precise InRelease                                           
Hit http://archive.ubuntu.com/ubuntu xenial InRelease                                              
Hit http://repository.spotify.com stable InRelease                                                 
Hit http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease                          
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]                           
Hit http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu xenial InRelease                      
Hit http://archive.canonical.com/ubuntu xenial InRelease                                           
Hit https://repo.skype.com/deb stable InRelease                                                    
Hit http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease                              
Get:2 http://archive.ubuntu.com/ubuntu xenial-security InRelease [107 kB]                          
Get:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]                         
Fetched 323 kB in 0s (0 B/s)                                                                       
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

```
and is more or less the same as posted here:
[Get:2 Upgrade tool [1.258 kB] Fetched 1.258 kB in 0s (0 B/s)authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg'extracting 'bionic.tar.gz'Reading cacheChecking package manager Reading package lists... Done Building dependency tree Reading state information... Done Hit [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InReleaseHit [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease Hit [http://repository.spotify.com](http://repository.spotify.com) stable InReleaseHit [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial InRelease Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease [109 kB]Hit [http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu](http://ppa.launchpad.net/ubuntuhandbook1/audacity/ubuntu) xenial InRelease Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InReleaseHit [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease Hit [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) xenial InRelease Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease [107 kB] Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease [107 kB]Fetched 323 kB in 0s (0 B/s)Reading package lists... Done Building dependency tree Reading state information... DoneRestoring original system stateAborting Reading package lists... Done Building dependency tree Reading state information... Done"]https://askubuntu.com/questions/1064080/problem-in-upgrading-16-04-to-18-04]("http://$ do-release-upgradeChecking for a new Ubuntu release Get:1 Upgrade tool signature [819 B)

I have tried upgrading from a live USB, but the upgrade option was not available.
As I am quite sure that the upgrade is available (I do get the notification), what could cause the system to become not upgradeable? Should I remove some of the PPAs or just do a clean install?

Help would be appreciated! 
 
P.S. If it matters, I have a dual boot system with Windows on the other partition.

---

### Post by kc1di on 2018-08-21
If it were me I'd back up any important files an do a fresh install, assuming or course the live session works well. good luck.

---

### Post by PaulW2U on 2018-08-21
> **tehmeh2 said:**
> Should I remove some of the PPAs or just do a clean install?
The upgrader should be able to deal with PPAs and will normally disable them if you don't remove them yourself.

May be it is confused by the **precise** PPA but your remaining sources and PPAs are for the **xenial** release? You could disable that one in Software & Updates and try upgrading again. If that doesn't work then a fresh installation might be the quickest way to get 18.04 running in the absence of any clear reason why the upgrade process can't continue.

---

### Post by tehmeh2 on 2018-08-22
Thank you for your replies!
Disabling **precise **did not help. I guess I'll have to do a fresh install at some point.

---

### Post by tehmeh2 on 2018-08-24
Somewhat accidentally I stumbled upon the cause of the issue. I think, that my installations of python (2 and 3) were not clean or in some sort of conflict. After removing/reinstalling these via [CODE] sudo apt-get [\CODE] I was able to upgrade the system.

I noticed that there were problems with python when I tried to launch resetter ([https://github.com/gaining/Resetter](https://github.com/gaining/Resetter)).
Also, removing and installing python caused a lot of apps to be removed along with it and I was somewhat forced to upgrade.

---

