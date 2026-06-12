---
title: "Cannot re-install or remove tomcat6"
date: 2012-04-03
forum: Installation &amp; Upgrades
---

### Post by misaki09 on 2012-04-03
**Hi!** 

Please help me clean uninstall tomcat6.

**I am installing tomcat6 using synaptic manager in ubuntu 11.10 and it was unsuccessful. So i tried to reinstall it still in synaptic manager but it returns an error:**

E: man-db: subprocess installed post-installation script returned error exit status 1
E: tomcat6: subprocess installed post-installation script returned error exit status 1

**Details:**
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 man-db
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

[B]I tried removing the tomcat6 package using terminal commands with:  
                         sudo aptitude remove tomcat6 --purge

But it returns:

[/B]The following packages will be REMOVED:  
  tomcat6 
The following partially installed packages will be configured:
  man-db 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 315 kB will be freed.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
(Reading database ... 448817 files and directories currently installed.)
Removing tomcat6 ...
id: tomcat6: No such user
dpkg: error processing tomcat6 (--remove):
 subprocess installed pre-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db[B]

So i tried: sudo fuser -v /var/cache/debconf/config.dat [/B]to find out which process is using this file.
[B]
It returns:
[/B]    Cannot stat /var/cache/debconf/config.dat: Bad address**I also tried:** **sudo killall apt-get**
[B]It returns:
[/B]apt-get: no process found
[B]
I also tried:[/B] **sudo aptitude autoclean** 
**It returns:**
Freed 0 B of disk space
[B]I also tried:  sudo dpkg --configure -a

It returns:[/B]

Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:

man-d

**I tried: sudo dpkg -i /var/cache/****apt/archives/*****deb**

**It returns:**
dpkg: error processing /var/cache/apt/archives/*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*deb

[B]I also tried: sudo mv /var/cache/debconf ~/; sudo apt-get install -f

But still it returns:[/B]
mv: cannot stat `/var/cache/debconf': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 tomcat6
E: Sub-process /usr/bin/dpkg returned an error code (1)
[B]
This is the full output of my cat /etc/apt/sources.list[/B]

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) oneiric-backports restricted main multiverse universe

Thank you!

---

### Post by raja.genupula on 2012-04-03
> **I tried: sudo dpkg -i /var/cache/****apt/archives/*****deb**

**It returns:**
dpkg: error processing /var/cache/apt/archives/*deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/*deb

actually that command should be as this 
**sudo dpkg -i /var/cache/****apt/archives/**[B]*.deb

[/B]you missed DOT at DEB . 
and while coming to your issue , its a bug actually and got fixed .
open your terminal and do this ```
sudo  rm -rf /var/cache/debconf/*
 sudo apt-get install -f

```

all the best .

---

### Post by misaki09 on 2012-04-03
Thank you!

---

### Post by misaki09 on 2012-04-03
**Hi! I tried your codes and this is the output:**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up localepurge (0.6.2+nmu2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing localepurge (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up tomcat6 (6.0.32-5ubuntu1.2) ...
debconf: DbDriver "config": could not open /var/cache/debconf/config.dat
dpkg: error processing tomcat6 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 localepurge
 tomcat6
 No /etc/locale.nopurge file present, exiting ...
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

