---
title: "synaptics didn't work"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by whaticansay on 2011-06-15
Hey Friends,

I had ubuntu installed as a guest on virtualbox 4.0.6 plus winXP as the host. 
For the past 2 days I was trying to install&update some packages but just can not get synaptics work.  Any suggestions? Thanks. 




uname -a

Linux FreeSurfer 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux






cat /etc/apt/sources.list

# deb cdrom:[Xubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse






sudo apt-get update

Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
  404 Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
  404 Not Found [IP: 91.189.92.169 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.169 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.





sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ajgreeny on 2011-06-15
Ubuntu 9.04 jaunty is no longer supported, so you will be out of luck.  I suggest a full backup of your home then a clean install of 10.04 which has nearly another two years support on the desktop, or if you want to try unity, go to 11.04.  You will not be able to upgrade in one go to either of those, hence my suggestion of a clean install.

If you don't already have a separate /home partition, I recommend you make one when you install this time, then restore your backed up home to that new /home partition after installing.
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

