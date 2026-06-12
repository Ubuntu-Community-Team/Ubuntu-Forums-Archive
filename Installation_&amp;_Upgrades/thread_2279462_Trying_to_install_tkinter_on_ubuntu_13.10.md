---
title: "Trying to install tkinter on ubuntu 13.10"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2015-05-23
HI all
 i am trying to install tkinter and wxpython packages on python 13.10 but i always receive this error 
wxpython

[PHP]marco@marco-Satellite-L40:/etc/apt$ sudo apt-get install python-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libhawtjni-runtime-java libjansi-java libjansi-native-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  blt tk8.5 tk8.5-lib
Suggested packages:
  blt-demo tix python-tk-dbg
The following NEW packages will be installed
  blt python-tk tk8.5 tk8.5-lib
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,871 kB of archives.
After this operation, 5,473 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  tk8.5-lib tk8.5 blt python-tk

Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com/ubuntu/ saucy/main tk8.5-lib i386 8.5.11-2ubuntu4
  404  Not Found [IP: 91.189.92.200 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy/main tk8.5 i386 8.5.11-2ubuntu4
  404  Not Found [IP: 91.189.92.200 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy/main blt i386 2.4z-7
  404  Not Found [IP: 91.189.92.200 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy/main python-tk i386 2.7.4-0ubuntu1
  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tk8.5/tk8.5-lib_8.5.11-2ubuntu4_i386.deb  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/tk8.5/tk8.5_8.5.11-2ubuntu4_i386.deb  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/blt/blt_2.4z-7_i386.deb  404  Not Found [IP: 91.189.92.200 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/p/python-stdlib-extensions/python-tk_2.7.4-0ubuntu1_i386.deb  404  Not Found [IP: 91.189.92.200 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
marco@marco-Satellite-L40:/etc/apt$ 
[/PHP]


[PHP]marco@marco-Satellite-L40:/etc/apt$ sudo apt-get install python-wxgtk2.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libhawtjni-runtime-java libjansi-java libjansi-native-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwxbase2.8-0 libwxgtk-media2.8-0 libwxgtk2.8-0 python-wxversion
Suggested packages:
  wx2.8-doc wx2.8-examples editra
The following NEW packages will be installed
  libwxbase2.8-0 libwxgtk-media2.8-0 libwxgtk2.8-0 python-wxgtk2.8 python-wxversion
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,903 kB of archives.
After this operation, 32.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  libwxbase2.8-0 libwxgtk2.8-0 libwxgtk-media2.8-0 python-wxversion python-wxgtk2.8
Install these packages without verification [y/N]? y
Err http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libwxbase2.8-0 i386 2.8.12.1-14ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libwxgtk2.8-0 i386 2.8.12.1-14ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe libwxgtk-media2.8-0 i386 2.8.12.1-14ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe python-wxversion all 2.8.12.1-14ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Err http://gb.archive.ubuntu.com/ubuntu/ saucy-updates/universe python-wxgtk2.8 i386 2.8.12.1-14ubuntu1.1
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxbase2.8-0_2.8.12.1-14ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxgtk2.8-0_2.8.12.1-14ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/libwxgtk-media2.8-0_2.8.12.1-14ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxversion_2.8.12.1-14ubuntu1.1_all.deb  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/universe/w/wxwidgets2.8/python-wxgtk2.8_2.8.12.1-14ubuntu1.1_i386.deb  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch som[/e archives, maybe run apt-get update or try with --fix-missing?
marco@marco-Satellite-L40:/etc/apt$ 
[/PHP]

is there something wrong wtih my sources list? 

kind regards
 marco

sources.list

[PHP]# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release i386 (20131016.1)]/ saucy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy universe
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu saucy partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main
[/PHP]

---

### Post by Bashing-om on 2015-05-23
mmistroni; Hey;

Nothing is wrong with the source.list;
The fault lies in running an End_Of_Life release.
13.10 is no longer supported and the software repository has been turned away.

Suggestion:
fresh install of a current release .

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

