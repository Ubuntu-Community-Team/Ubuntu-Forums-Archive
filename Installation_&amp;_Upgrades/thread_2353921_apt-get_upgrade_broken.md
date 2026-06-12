---
title: "apt-get upgrade broken"
date: 2017-02-26
forum: Installation &amp; Upgrades
---

### Post by biarkivior on 2017-02-26
so i am having some issues upgrading and updating. background. 14.04 crashed during upgrade to 16 "had a power outage". got Ubuntu up and running but updates seem broken. did a little research and need some help even though soome commands were for 14 i was hoping someone else ran in to the problem and solved it. 



```
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
(Reading database ... 1151066 files and directories currently installed.)
Preparing to unpack .../kodi_2%3a17.0~git20170210.1529-final-0xenial_all.deb ...
Unpacking kodi (2:17.0~git20170210.1529-final-0xenial) ...
dpkg: error processing archive /var/cache/apt/archives/kodi_2%3a17.0~git20170210.1529-final-0xenial_all.deb (--unpack):
 trying to overwrite '/usr/share/xsessions/kodi.desktop', which is also in package kodi-data 15.2+dfsg1-3ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kodi_2%3a17.0~git20170210.1529-final-0xenial_all.deb
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
E: Sub-process /usr/bin/dpkg returned an error code (1)
owner@owner-Ubuntu:~$ sudo apt-get update
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:7 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease           
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Fetched 204 kB in 1s (191 kB/s)                              
Reading package lists... Done
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```
```
owner@owner-Ubuntu:~$ sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.distrib
rm: cannot remove '/etc/apt/apt.conf.d/50unattended-upgrades.distrib': No such file or directory
owner@owner-Ubuntu:~$ sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.distrib
rm: cannot remove '/etc/apt/apt.conf.d/50unattended-upgrades.distrib': No such file or directory
```
```
owner@owner-Ubuntu:~$ ls -l /etc/apt/apt.conf.d/
total 68
-rw-rw-r-- 1 root root    49 Feb 15  2016 00aptitude
-rw-rw-r-- 1 root root    40 Feb 15  2016 00trustcdrom
-rw-r--r-- 1 root root   769 Jan 18 06:24 01autoremove
-r--r--r-- 1 root root 14518 Feb 22 17:23 01autoremove-kernels
-rw-r--r-- 1 root root    42 Jan 18 06:24 01-vendor-ubuntu
-rw-r--r-- 1 root root   129 Aug 22  2011 10periodic
-rw-r--r-- 1 root root   108 Aug 22  2011 15update-stamp
-rw-r--r-- 1 root root    85 Aug 22  2011 20archive
-rw-r--r-- 1 root root   243 Mar 11  2013 20dbus
-rw-r--r-- 1 root root  1432 Apr 18  2016 50appstream
-rw-r--r-- 1 root root  2331 Jun 22  2015 50unattended-upgrades
-rw-r--r-- 1 root root  2367 Feb  9 15:40 50unattended-upgrades.ucf-dist
-rw-r--r-- 1 root root   182 Feb 23  2014 70debconf
-rw-r--r-- 1 root root   305 May 24  2016 99update-notifier
```

---

### Post by Bashing-om on 2017-02-26
biarkivior; Hello;

Does not appear to badly broken .
The main thing the system is hollering about is kodi .
-  Ignoring file '50unattended-upgrades.ucf-dist' - is a warning, not an error, and for now will not effect the resolving the packages .
Let's begin at kodi (PPA ??):
Post back the returns - Between Code Tags - of terminal commands:
```

apt-cache policy kodi
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and make sure all the sources are consistent.

Once sources are in a consistent state we see what condition the package manager is in.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2017-02-26
Welcome. Also, try these three, in this order, and post back any errors any of them throw.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

---

### Post by deadflowr on 2017-02-26
There seems to be a conflict between the kodi package from the xbmc-team ppa and kodi-data package from the Ubuntu repositories.
I'd try removing the kodi-data package as there is no kodi-data package in the xbmc-team ppa, therefor it's functions seem to be builtin directly into the kodi package from the xbmc-team ppa.
If that makes sense.

---

### Post by biarkivior on 2017-02-26
1st command
```
owner@owner-Ubuntu:~$ apt-cache policy kodi
kodi:
  Installed: (none)
  Candidate: 2:17.0~git20170210.1529-final-0xenial
  Version table:
     2:17.0~git20170210.1529-final-0xenial 500
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 Packages
        500 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main i386 Packages
     15.2+dfsg1-3ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$ 
```


this is what i get after 2nd command 

```
 1    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     2    
     3    # newer versions of the distribution.
     4    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     5    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     6    
     7    ## Major bug fix updates produced after the final release of the
     8    ## distribution.
     9    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    10    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    11    
    12    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    13    ## team. Also, please note that software in universe WILL NOT receive any
    14    ## review or updates from the Ubuntu security team.
    15    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    16    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    17    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    18    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    19    
    20    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21    ## team, and may not be under a free licence. Please satisfy yourself as to 
    22    ## your rights to use the software. Also, please note that software in 
    23    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    24    ## security team.
    25    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    26    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    27    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    28    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    36    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    37    
    38    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    39    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    40    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    41    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    42    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    43    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    44    
    45    ## Uncomment the following two lines to add software from Canonical's
    46    ## 'partner' repository.
    47    ## This software is not part of Ubuntu, but is offered by Canonical and the
    48    ## respective vendors as a service to Ubuntu users.
    49    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    50    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    51    
```

3rd command
```
owner@owner-Ubuntu:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/dropbox.list <==
# deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/dropbox.list.distUpgrade <==
deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) trusty main


==> /etc/apt/sources.list.d/dropbox.list.save <==
# deb [arch=i386,amd64] [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) xenial main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/playonlinux.list <==
# deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/playonlinux.list.distUpgrade <==
deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise main


==> /etc/apt/sources.list.d/playonlinux.list.save <==
# deb [http://deb.playonlinux.com/](http://deb.playonlinux.com/) precise main # disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_billiards_ubuntu.list <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_billiards_ubuntu.list.distUpgrade <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_billiards_ubuntu.list.save <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/billiards/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_bionightmarelite_ubuntu.list <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_bionightmarelite_ubuntu.list.distUpgrade <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_bionightmarelite_ubuntu.list.save <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list.distUpgrade <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf


==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list.save <==
# deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) xenial main #Added by software-center; credentials stored in /etc/apt/auth.conf disabled on upgrade to xenial


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/team-xbmc-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) trusty main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list <==
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main


==> /etc/apt/sources.list.d/team-xbmc-ubuntu-ppa-xenial.list.save <==
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial main


==> /etc/apt/sources.list.d/upubuntu-com-gtk3-trusty.list <==
# deb [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main


==> /etc/apt/sources.list.d/upubuntu-com-gtk3-trusty.list.distUpgrade <==
deb [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main


==> /etc/apt/sources.list.d/upubuntu-com-gtk3-trusty.list.save <==
# deb [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) xenial main # disabled on upgrade to xenial
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu](http://ppa.launchpad.net/upubuntu-com/gtk3/ubuntu) trusty main
```

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> There seems to be a conflict between the kodi package from the xbmc-team ppa and kodi-data package from the Ubuntu repositories.
I'd try removing the kodi-data package as there is no kodi-data package in the xbmc-team ppa, therefor it's functions seem to be builtin directly into the kodi package from the xbmc-team ppa.
If that makes sense.

so
it seems that i dont understand what youre saying as i am newish to ubuntu and ive only been using it a year

---

### Post by deadflowr on 2017-02-26
> **biarkivior said:**
> so
it seems that i dont understand what youre saying as i am newish to ubuntu and ive only been using it a year

What I said was there is some conflict between two different packages.
kodi and kodi-data.
The kodi package is coming from the ppa.

But the ppa does not have a kodi-data package.
That package is available in the regular Ubuntu repositories.

It would seem you have the kodi-data package already installed, which is causing the kodi package from the ppa to fail to install.

check what kodi packages are installed, if any, with
```
dpkg -l | grep kodi 
```
post the results

edit: looking at the kodi howto here: [http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux]("http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux")
they stipulate this in red:
> Some (later) Ubuntu versions include Kodi built by Ubuntu themselves. If you have installed Ubuntu Kodi, please remove the packages "kodi kodi-bin kodi-data" before trying to install team-xbmc PPA packages.

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> What I said was there is some conflict between two different packages.
kodi and kodi-data.
The kodi package is coming from the ppa.

But the ppa does not have a kodi-data package.
That package is available in the regular Ubuntu repositories.

It would seem you have the kodi-data package already installed, which is causing the kodi package from the ppa to fail to install.

check what kodi packages are installed, if any, with
```
dpkg -l | grep kodi 
```
post the results

edit: looking at the kodi howto here: [http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux)
they stipulate this in red:
owner@owner-Ubuntu:~$ dpkg -l | grep kodi
ic  kodi                                            15.2+dfsg1-3ubuntu1                           amd64        Open Source Home Theatre (executable binaries)
owner@owner-Ubuntu:~$

---

### Post by deadflowr on 2017-02-26
> **biarkivior said:**
> owner@owner-Ubuntu:~$ dpkg -l | grep kodi
ic  kodi                                            15.2+dfsg1-3ubuntu1                           amd64        Open Source Home Theatre (executable binaries)
owner@owner-Ubuntu:~$

okay try this to try and purge the kodi package completely:
```
dpkg -l | grep kodi | awk '{print $2}' | xargs sudo apt-get purge -s
```
this command is a dry-run command and will list all packages that will be removed.
If the list seems good (post if you do not know) then try the real command
```
dpkg -l | grep kodi | awk '{print $2}' | xargs sudo apt-get purge -y
```
then try reinstalling kodi and see what happens.

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> What I said was there is some conflict between two different packages.
kodi and kodi-data.
The kodi package is coming from the ppa.

But the ppa does not have a kodi-data package.
That package is available in the regular Ubuntu repositories.

It would seem you have the kodi-data package already installed, which is causing the kodi package from the ppa to fail to install.

check what kodi packages are installed, if any, with
```
dpkg -l | grep kodi 
```
post the results

edit: looking at the kodi howto here: [http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux)
they stipulate this in red:

ive tried removing it and this is what is happening. ive tried uninstalling it before to get a fresh install

owner@owner-Ubuntu:~$ sudo apt-get remove kodi
[sudo] password for owner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'kodi' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$ sudoapt-get remove --auto-remove kodi
sudoapt-get: command not found
owner@owner-Ubuntu:~$ sudo apt-get --auto-remove kodi
E: Command line option --auto-remove is not understood in combination with the other options
owner@owner-Ubuntu:~$

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> okay try this to try and purge the kodi package completely:
```
dpkg -l | grep kodi | awk '{print $2}' | xargs sudo apt-get purge -s
```
this command is a dry-run command and will list all packages that will be removed.
If the list seems good (post if you do not know) then try the real command
```
dpkg -l | grep kodi | awk '{print $2}' | xargs sudo apt-get purge -y
```
then try reinstalling kodi and see what happens.

tried everything i know and read


Reading state information... Done
The following packages will be REMOVED:
  kodi*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg kodi
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$ 1
1: command not found
owner@owner-Ubuntu:~$ dpkg -l | grep kodi | awk '{print $2}' | xargs sudo apt-get purge -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kodi*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 1034887 files and directories currently installed.)
Removing kodi (15.2+dfsg1-3ubuntu1) ...
Purging configuration files for kodi (15.2+dfsg1-3ubuntu1) ...
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$

---

### Post by deadflowr on 2017-02-26
> N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
Do not worry about that line, it's only a warning and can be dealt with whenever.
It's not related to the real issue which is fixing kodi.

Now that kodi has been removed what happens when you try to install kodi?

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> Do not worry about that line, it's only a warning and can be dealt with whenever.
It's not related to the real issue which is fixing kodi.

Now that kodi has been removed what happens when you try to install kodi?

it seems its still doing this
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  javascript-common kodi-bin libcec4 libcrossguid1 libjs-jquery
  libmicrohttpd10 libmysqlclient20 libnfs8 libp8-platform2 libpcrecpp0v5
  libshairplay0 libtinyxml2.6.2v5 libva-drm1 libva-x11-1 libvdpau1
  mesa-vdpau-drivers mysql-common python-bluez python-simplejson
  vdpau-driver-all
Suggested packages:
  apache2 | lighttpd | httpd kodi-pvr-mythtv kodi-pvr-vuplus kodi-pvr-vdr-vnsi
  kodi-pvr-njoy kodi-pvr-nextpvr kodi-pvr-mediaportal-tvserver
  kodi-pvr-tvheadend-hts kodi-pvr-dvbviewer kodi-pvr-argustv
  kodi-pvr-iptvsimple kodi-audioencoder-vorbis kodi-audioencoder-flac
  kodi-audioencoder-lame libvdpau-va-gl1 nvidia-vdpau-driver
  nvidia-legacy-340xx-vdpau-driver
Recommended packages:
  libva-intel-vaapi-driver
The following NEW packages will be installed:
  javascript-common kodi kodi-bin libcec4 libcrossguid1 libjs-jquery
  libmicrohttpd10 libmysqlclient20 libnfs8 libp8-platform2 libpcrecpp0v5
  libshairplay0 libtinyxml2.6.2v5 libva-drm1 libva-x11-1 libvdpau1
  mesa-vdpau-drivers mysql-common python-bluez python-simplejson
  vdpau-driver-all
0 upgraded, 21 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,352 kB/36.0 MB of archives.
After this operation, 104 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libpcrecpp0v5 amd64 2:8.38-3.1 [15.2 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 javascript-common all 11 [6,066 B]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 libmicrohttpd10 amd64 0.9.44+dfsg-1ubuntu2 [43.9 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 mysql-common all 5.7.17-0ubuntu0.16.04.1 [15.1 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libmysqlclient20 amd64 5.7.17-0ubuntu0.16.04.1 [809 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libtinyxml2.6.2v5 amd64 2.6.2-3 [29.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 libva-drm1 amd64 1.7.0-1 [8,414 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 libva-x11-1 amd64 1.7.0-1 [11.9 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libvdpau1 amd64 1.1.1-3ubuntu1 [25.5 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 python-bluez amd64 0.22-1 [47.3 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 python-simplejson amd64 3.8.1-1ubuntu2 [60.4 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 libnfs8 amd64 1.9.8-1 [62.0 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 libjs-jquery all 1.11.3+dfsg-4 [161 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 vdpau-driver-all amd64 1.1.1-3ubuntu1 [4,674 B]
Get:15 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 libcrossguid1 amd64 0.1~git20150807.8f399e8~xenial [6,130 B]
Get:16 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial/main amd64 libshairplay0 amd64 0.9.0.1-2~xenial [45.4 kB]
Fetched 1,352 kB in 6s (223 kB/s)                                              
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
Selecting previously unselected package libpcrecpp0v5:amd64.
(Reading database ... 1034889 files and directories currently installed.)
Preparing to unpack .../libpcrecpp0v5_2%3a8.38-3.1_amd64.deb ...
Unpacking libpcrecpp0v5:amd64 (2:8.38-3.1) ...
Selecting previously unselected package javascript-common.
Preparing to unpack .../javascript-common_11_all.deb ...
Unpacking javascript-common (11) ...
Selecting previously unselected package libcrossguid1:amd64.
Preparing to unpack .../libcrossguid1_0.1~git20150807.8f399e8~xenial_amd64.deb ...
Unpacking libcrossguid1:amd64 (0.1~git20150807.8f399e8~xenial) ...
Selecting previously unselected package libmicrohttpd10.
Preparing to unpack .../libmicrohttpd10_0.9.44+dfsg-1ubuntu2_amd64.deb ...
Unpacking libmicrohttpd10 (0.9.44+dfsg-1ubuntu2) ...
Selecting previously unselected package mysql-common.
Preparing to unpack .../mysql-common_5.7.17-0ubuntu0.16.04.1_all.deb ...
Unpacking mysql-common (5.7.17-0ubuntu0.16.04.1) ...
Selecting previously unselected package libmysqlclient20:amd64.
Preparing to unpack .../libmysqlclient20_5.7.17-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libmysqlclient20:amd64 (5.7.17-0ubuntu0.16.04.1) ...
Selecting previously unselected package libtinyxml2.6.2v5:amd64.
Preparing to unpack .../libtinyxml2.6.2v5_2.6.2-3_amd64.deb ...
Unpacking libtinyxml2.6.2v5:amd64 (2.6.2-3) ...
Selecting previously unselected package libva-drm1:amd64.
Preparing to unpack .../libva-drm1_1.7.0-1_amd64.deb ...
Unpacking libva-drm1:amd64 (1.7.0-1) ...
Selecting previously unselected package libva-x11-1:amd64.
Preparing to unpack .../libva-x11-1_1.7.0-1_amd64.deb ...
Unpacking libva-x11-1:amd64 (1.7.0-1) ...
Selecting previously unselected package libvdpau1:amd64.
Preparing to unpack .../libvdpau1_1.1.1-3ubuntu1_amd64.deb ...
Unpacking libvdpau1:amd64 (1.1.1-3ubuntu1) ...
Selecting previously unselected package kodi-bin.
Preparing to unpack .../kodi-bin_2%3a17.0~git20170210.1529-final-0xenial_amd64.deb ...
Unpacking kodi-bin (2:17.0~git20170210.1529-final-0xenial) ...
Selecting previously unselected package python-bluez.
Preparing to unpack .../python-bluez_0.22-1_amd64.deb ...
Unpacking python-bluez (0.22-1) ...
Selecting previously unselected package python-simplejson.
Preparing to unpack .../python-simplejson_3.8.1-1ubuntu2_amd64.deb ...
Unpacking python-simplejson (3.8.1-1ubuntu2) ...
Selecting previously unselected package libnfs8:amd64.
Preparing to unpack .../libnfs8_1.9.8-1_amd64.deb ...
Unpacking libnfs8:amd64 (1.9.8-1) ...
Selecting previously unselected package libshairplay0:amd64.
Preparing to unpack .../libshairplay0_0.9.0.1-2~xenial_amd64.deb ...
Unpacking libshairplay0:amd64 (0.9.0.1-2~xenial) ...
Selecting previously unselected package libp8-platform2:amd64.
Preparing to unpack .../libp8-platform2_2.1.0.1~xenial_amd64.deb ...
Unpacking libp8-platform2:amd64 (2.1.0.1~xenial) ...
Selecting previously unselected package libcec4:amd64.
Preparing to unpack .../libcec4_4.0.1.1~xenial_amd64.deb ...
Unpacking libcec4:amd64 (4.0.1.1~xenial) ...
Selecting previously unselected package kodi.
Preparing to unpack .../kodi_2%3a17.0~git20170210.1529-final-0xenial_all.deb ...
Unpacking kodi (2:17.0~git20170210.1529-final-0xenial) ...
Selecting previously unselected package libjs-jquery.
Preparing to unpack .../libjs-jquery_1.11.3+dfsg-4_all.deb ...
Unpacking libjs-jquery (1.11.3+dfsg-4) ...
Selecting previously unselected package mesa-vdpau-drivers:amd64.
Preparing to unpack .../mesa-vdpau-drivers_12.0.6-0ubuntu0.16.04.1_amd64.deb ...
Unpacking mesa-vdpau-drivers:amd64 (12.0.6-0ubuntu0.16.04.1) ...
Selecting previously unselected package vdpau-driver-all:amd64.
Preparing to unpack .../vdpau-driver-all_1.1.1-3ubuntu1_amd64.deb ...
Unpacking vdpau-driver-all:amd64 (1.1.1-3ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up libpcrecpp0v5:amd64 (2:8.38-3.1) ...
Setting up javascript-common (11) ...
Setting up libcrossguid1:amd64 (0.1~git20150807.8f399e8~xenial) ...
Setting up libmicrohttpd10 (0.9.44+dfsg-1ubuntu2) ...
Setting up mysql-common (5.7.17-0ubuntu0.16.04.1) ...
update-alternatives: using /etc/mysql/my.cnf.fallback to provide /etc/mysql/my.cnf (my.cnf) in auto mode
Setting up libmysqlclient20:amd64 (5.7.17-0ubuntu0.16.04.1) ...
Setting up libtinyxml2.6.2v5:amd64 (2.6.2-3) ...
Setting up libva-drm1:amd64 (1.7.0-1) ...
Setting up libva-x11-1:amd64 (1.7.0-1) ...
Setting up libvdpau1:amd64 (1.1.1-3ubuntu1) ...
Setting up kodi-bin (2:17.0~git20170210.1529-final-0xenial) ...
Setting up python-bluez (0.22-1) ...
Setting up python-simplejson (3.8.1-1ubuntu2) ...
Setting up libnfs8:amd64 (1.9.8-1) ...
Setting up libshairplay0:amd64 (0.9.0.1-2~xenial) ...
Setting up libp8-platform2:amd64 (2.1.0.1~xenial) ...
Setting up libcec4:amd64 (4.0.1.1~xenial) ...
Setting up kodi (2:17.0~git20170210.1529-final-0xenial) ...
Setting up libjs-jquery (1.11.3+dfsg-4) ...
Setting up mesa-vdpau-drivers:amd64 (12.0.6-0ubuntu0.16.04.1) ...
Setting up vdpau-driver-all:amd64 (1.1.1-3ubuntu1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
```

---

### Post by deadflowr on 2017-02-26
**(Please use code tags)

Well it seems to have installed fine.

If you run the commands Bucky Ball asked earlier, are there any errors from those, now?
(In particular run the second and third commands, the
```
sudo apt update
sudo apt full-upgrade
```
commands)

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> **(Please use code tags)

Well it seems to have installed fine.

If you run the commands Bucky Ball asked earlier, are there any errors from those, now?
(In particular run the second and third commands, the
```
sudo apt update
sudo apt full-upgrade
```
commands)

ok
 it seems i now have kodi now to install the rest of the plugins

```
owner@owner-Ubuntu:~$ sudo apt update[sudo] password for owner: 
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                     
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease             
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Hit:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                     
Hit:8 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) xenial InRelease           
Hit:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease           
Fetched 102 kB in 0s (105 kB/s)                                                
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$
```

---

### Post by deadflowr on 2017-02-26
Sounds good.

If you want to remove that pesky line that keeps showing up run
```
sudo rm /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
```

your original post ran the wrong file name.

(50unattended-upgrades.distrib is make-believe, as in it does not nor never has existed)

But you were really close.

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> Sounds good.

If you want to remove that pesky line that keeps showing up run
```
sudo rm /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
```

your original post ran the wrong file name.

(50unattended-upgrades.distrib is make-believe, as in it does not nor never has existed)

But you were really close.
 

thank you so much  i dont care about the message at this time it s not causing any problems. 
owner@owner-Ubuntu:~$ sudo apt-get upgrade
[sudo] password for owner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
owner@owner-Ubuntu:~$ sudo rm /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
> sudo rm /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
rm: cannot remove '/etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist'$'\n''sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist': No such file or directory
owner@owner-Ubuntu:~$

---

### Post by deadflowr on 2017-02-26
Sorry I added the ' to the filename
it should be
 /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
I added the ' so it looks like
 /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
see the ' next to the 50, like '50.
try again without that symbol.

---

### Post by biarkivior on 2017-02-26
> **deadflowr said:**
> Sorry I added the ' to the filename
it should be
 /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
I added the ' so it looks like
 /etc/apt/apt.conf.d/'50unattended-upgrades.ucf-dist
see the ' next to the 50, like '50.
try again without that symbol.
owner@owner-Ubuntu:~$ /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
bash: /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist: Permission denied

---

### Post by ian-weisser on 2017-02-26
By now, you should understand what a 'Permission denied' error means, and how to get past it by using sudo.

---

### Post by deadflowr on 2017-02-26
> **biarkivior said:**
> owner@owner-Ubuntu:~$ /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
bash: /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist: Permission denied

Sometimes I think things are obvious, based on all previous inputs, but
you needed to run the sudo rm command with the new filename instead of with the broken name i listed before.
```
sudo rm /etc/apt/apt.conf.d/50unattended-upgrades.ucf-dist
```
the original command added a character that messed the name.
Sorry for the lack of clarity on that.
mea culpa

---

### Post by nikosf100 on 2017-08-31
I removed Kodi !7.1
I tryed to reinstall Kodi 17.4 and got this:

nikos@nikos-Presario-CQ58-Notebook-PC:~$ sudo add-apt-repository ppa:team-xbmc/kodi-old

 
 More information: [https://launchpad.net/~team-xbmc/+archive/ubuntu/kodi-old](https://launchpad.net/~team-xbmc/+archive/ubuntu/kodi-old)
Press [ENTER] to continue or ctrl-c to cancel the plugin

"gpg: keybox '/tmp/tmp4_adn9lt/pubring.gpg' created
gpg: /tmp/tmp4_adn9lt/trustdb.gpg: &#948;&#951;&#956;&#953;&#959;&#965;&#961;&#947;&#942;&#952;&#951;&#954;&#949; &#951; trustdb
gpg: key 6D975C4791E7EE5E: public key "Launchpad PPA for XBMC for Linux" imported
gpg: No trusted keys were found
gpg: Total number processed: 1  
gpg:               Imported: 1
OK"

I tryed to install with Kodi.deb but it stops to 9%

I did all these :

"sudo apt autoremove
sudo apt remove kodi kodi-bin kodi-data
sudo apt install software-properties-common
sudo add-apt-repository ppa:team-xbmc/ppa
sudo apt update
sudo apt install kodi"

but nothing
How can I solve this problem?

---

