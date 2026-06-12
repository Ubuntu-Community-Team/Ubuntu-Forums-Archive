---
title: "How to fix the UPDATE and UPGRADE"
date: 2013-04-01
forum: Installation &amp; Upgrades
---

### Post by dputhal on 2013-04-01
deepakp@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

deepakp@ubuntu:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages             
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  404  Not Found [IP: 91.189.92.200 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
  404  Not Found [IP: 91.189.92.200 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.15 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by claracc on 2013-04-01
You haven't explained what your problem is and what do you want to do, neither add any information about your hardware specifications, so it is difficult to help in these conditions.

Anycase, if you are trying to update your ¿ maverick? ubuntu release, you have to know that ubuntu 10.10 has reached its end of life, so the repositories you are trying to use are not available.

I f you want to update to a newer release I think you'll have to do a new fresh install. Here, you have documentation: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) to know more about the problem.

---

### Post by dputhal on 2013-04-01
I have this configuration and I want to install this because my software/platform support this version. 

Can you please help me. I am finding the above errors during update. 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

deepakp@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by claracc on 2013-04-01
As I have said in my previous post, you are trying to install ubuntu maverick, which has reached its end of life, so, you are not going to receive any security updates and the repositories you want to use are not in the in the urls addressed, so, for this rease you are finding 404 error, NOT FOUND.

I don't recommend to install an obsolete ubuntu distro as 10.10, but installing a stable supported release 12.04 or 12.10 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases).

Anycase, if you want ro install software in an obsolete release, you have to move the repositories in your sources.list file, as it is addressed in this link: [http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support).

---

