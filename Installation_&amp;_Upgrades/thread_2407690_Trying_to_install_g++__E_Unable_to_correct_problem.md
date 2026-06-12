---
title: "Trying to install g++  E: Unable to correct problems, you have held broken packages."
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by mm420 on 2018-12-07
I just did a fresh install of ubuntu server 18.04.  I am trying to install g++ (as well as a few other things) and keep running into this error: E: Unable to correct problems, you have held broken packages.

I have run the command ```
dpkg --get-selections | grep hold 
``` but there is no output.  I have also tried to use synaptic to fix the broken packages, but it was unable to.

Here is the content of my sources.list

```

# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe 
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse 
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse 

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse 
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu/ bionic partner 
# deb-src http://archive.canonical.com/ubuntu/ bionic partner 

deb http://security.ubuntu.com/ubuntu/ bionic-security main restricted 
# deb-src http://security.ubuntu.com/ubuntu/ bionic-security main restricted 
deb http://security.ubuntu.com/ubuntu/ bionic-security universe 
# deb-src http://security.ubuntu.com/ubuntu/ bionic-security universe 
deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse 
# deb-src http://security.ubuntu.com/ubuntu/ bionic-security multiverse 


```

Any suggestions?

---

### Post by deadflowr on 2018-12-07
Post back the output from
```
sudo apt update
sudo apt upgrade
```

---

### Post by mm420 on 2018-12-07
```
chase@anubis:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]                     
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                                                                                              
Hit:4 http://archive.canonical.com/ubuntu bionic InRelease                                                                                                                                
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                                                                        
Hit:6 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                        
Reading package lists... Done
E: Release file for http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease is not valid yet (invalid for another 47min 44s). Updates for this repository will not be applied.
E: Release file for http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease is not valid yet (invalid for another 47min 58s). Updates for this repository will not be applied.
E: Release file for http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease is not valid yet (invalid for another 48min 34s). Updates for this repository will not be applied.
chase@anubis:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by mm420 on 2018-12-07
I'm an idiot - the time was correct on my computer, but the timezone was not.  Once I corrected that so it could download those repos, things seem to be working

---

### Post by deadflowr on 2018-12-07
Looks like an issue with the clock settings.
Check the time is properly syncing:
[https://help.ubuntu.com/lts/serverguide/NTP.html.en]("https://help.ubuntu.com/lts/serverguide/NTP.html.en")
[https://askubuntu.com/questions/1059217/getting-release-is-not-valid-yet-while-updating-ubuntu-docker-container]("https://askubuntu.com/questions/1059217/getting-release-is-not-valid-yet-while-updating-ubuntu-docker-container")

Ninja'd


Edit: If you found the solution. then by all means please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

