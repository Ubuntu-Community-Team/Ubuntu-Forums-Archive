---
title: "Could not download all repository indexes"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by rajukakani on 2011-06-01
Hello All,

I am quite new to ubuntu, when I try to upgrade or install some new packages, I am getting the following error, Could  someone please help me to get rid of this problem.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.92.170). - connect (110: Connection timed out) [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.170 80]
Some index files failed to download, they have been ignored, or old ones used instea

I am  hereby giving my /etc/apt/sources.list file

# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid main restricted multiverse #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates universe

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
# deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security main restricted multiverse
deb [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse


Here  is the output of sudo apt-get update

Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid Release.gpg                         
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US      
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US   
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates Release.gpg                  
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security Release.gpg                 
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://kr.archive.ubuntu.com/ubuntu/](http://kr.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid Release                             
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates Release                                                       
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security Release                                                                
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid/main Packages                                                                   
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid/restricted Packages                 
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid/multiverse Packages                 
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid/universe Packages                   
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates/main Packages               
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates/restricted Packages         
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates/multiverse Packages          
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-updates/universe Packages            
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security/main Packages               
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg                            
  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (110: Connection timed out) [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty/multiverse Translation-en_US   
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg                    
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates/multiverse Translation-en_US
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://kr.archive.ubuntu.com](http://kr.archive.ubuntu.com) lucid-security/universe Packages
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.88.140). - connect (110: Connection timed out) [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.140 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Note: My  Internet connection is working fine.

Thanx & Regards
Raju

---

### Post by ikt on 2011-06-01
> **rajukakani said:**
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

you need to remove these from your sources.list

The majority of your sources.list is "lucid" but those specific lines try to update for "jaunty", which is no longer available.

---

### Post by rajukakani on 2011-06-01
Thank you very much for your help, Now sudo ap-get update got updates successfully and
I am able to install the new packages after removing the following lines from source.list file

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

But I am still facing the following problem in updating software sources. 

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.92.171). - connect (110: Connection timed out) [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]
Some index files failed to download, they have been ignored, or old ones used instead.

Please help me in this regard to resolve this problem.

Thanx & Regards
Raju

---

