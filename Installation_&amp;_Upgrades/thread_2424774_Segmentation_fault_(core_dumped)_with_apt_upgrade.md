---
title: "Segmentation fault (core dumped) with apt upgrade"
date: 2019-08-14
forum: Installation &amp; Upgrades
---

### Post by charlieg on 2019-08-14
Ubuntu 19.04, upgraded from 18.04.

```
root@charles-H310M:/home/charles# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 19.04
Release:	19.04
Codename:	disco
```

It has been working and updating fine since I started running the PC in May (bought it with Ubuntu pre-installed and manually upgraded from there). I go on holiday for a week or so, and come back and the update does this:

```
root@charles-H310M:/home/charles# apt update && apt upgrade
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco InRelease                                                                                 
Hit:3 [http://ppa.launchpad.net/damentz/liquorix/ubuntu](http://ppa.launchpad.net/damentz/liquorix/ubuntu) disco InRelease                                                                    
Hit:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco-updates InRelease                                                                         
Hit:5 [http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu](http://ppa.launchpad.net/oguzhaninan/stacer/ubuntu) disco InRelease                                                                  
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) disco-backports InRelease                                                                       
Ign:7 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) cosmic InRelease                                                                                    
Hit:8 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease                                                                         
Hit:9 [http://ppa.launchpad.net/openjdk-r/ppa/ubuntu](http://ppa.launchpad.net/openjdk-r/ppa/ubuntu) disco InRelease                                                                       
Get:10 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) cosmic Release [6,600 B]                                                                           
Hit:11 [http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu](http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu) disco InRelease                                                            
Hit:12 [http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu](http://ppa.launchpad.net/remmina-ppa-team/remmina-next/ubuntu) disco InRelease                                                      
Ign:13 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable InRelease                                                                                
Hit:14 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) disco InRelease                                                                   
Hit:15 [http://repo.vivaldi.com/stable/deb](http://repo.vivaldi.com/stable/deb) stable Release                                                                      
Hit:16 [http://archive.canonical.com](http://archive.canonical.com) disco InRelease                                                                           
Hit:17 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease                                                 
Hit:18 [https://wavebox.pro/dl/client/repo](https://wavebox.pro/dl/client/repo) x86_64/ InRelease                       
Fetched 6,600 B in 1s (5,433 B/s)           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
47 packages can be upgraded. Run 'apt list --upgradable' to see them.
Segmentation fault (core dumped)
E: Problem executing scripts APT::Update::Post-Invoke-Stats '[ ! -f /usr/lib/ubuntu-advantage/apt-esm-hook ] || /usr/lib/ubuntu-advantage/apt-esm-hook'
E: Sub-process returned an error code

```

So it seems the offending package is ubuntu-advantage-tools but I am hesitant to purge it as it is part of the ubuntu-minimal package which sounds kinda important.

Any suggestions?

---

### Post by charlieg on 2019-08-14
The standard software updater GUI worked. I just tried it on the off hand that it might give me more feedback, and it didn't encounter the error. Strange... but a solution of sorts, I guess.

---

### Post by dino99 on 2019-08-14
is 'journalctl -b' has logged something usefull ?

reported bug: [https://launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bugs](https://launchpad.net/ubuntu/+source/ubuntu-advantage-tools/+bugs)
(see bug 1840091)

---

### Post by charlieg on 2019-08-14
It pointed me to a crash dump but I'm not sure that in itself is particularly useful.

However since the update via the software updater GUI, the command line apt has returned to normality.

---

