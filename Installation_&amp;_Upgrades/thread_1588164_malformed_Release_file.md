---
title: "malformed Release file?"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by neopiper on 2010-10-04
Hi guys,

I have been having a problem everytime I try to update I recieve this msg.  

Failed to fetch [http://mirrors.ecvps.com/ubuntu/dists/lucid/Release](http://mirrors.ecvps.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  free/binary-amd64/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.


The output of my sudo apt-get update is as follows


Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid Release.gpg
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/main Translation-en_US              
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/restricted Translation-en_US        
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/multiverse Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/free Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid/non-free Translation-en_US
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates Release.gpg
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates/main Translation-en_US      
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security Release.gpg        
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security/main Translation-en_US     
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid Release
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates Release                             
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security Release                            
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/main Packages                               
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/restricted Packages         
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/universe Packages    
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/main Sources                                
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/restricted Sources                          
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/multiverse Packages                         
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid/multiverse Sources                          
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/main Packages                       
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/restricted Packages                 
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/main Sources 
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/restricted Sources
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/universe Packages                   
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/universe Sources                    
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/multiverse Packages                 
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-updates/multiverse Sources                  
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/main Packages
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/restricted Packages
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/universe Packages
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/main Sources
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/restricted Sources
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/multiverse Packages
Hit [http://mirrors.ecvps.com](http://mirrors.ecvps.com) lucid-security/multiverse Sources             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
W: Failed to fetch [http://mirrors.ecvps.com/ubuntu/dists/lucid/Release](http://mirrors.ecvps.com/ubuntu/dists/lucid/Release)  Unable to find expected entry  free/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


My sources.lst file is as follows...I notice that it says Ubuntu 9.04 though I updated from this one to 9.10 and then, the one I'm currently using is 10.04

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) lucid universe
# deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) lucid universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid multiverse
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted universe
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security main restricted
# deb [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) lucid-security universe
# deb-src [http://76.73.4.58/ubuntu/](http://76.73.4.58/ubuntu/) lucid-security universe
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
deb-src [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid-security multiverse
# deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) lucid main #GlobalMenu
# deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main #Global Menu (sources)
# deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) lucid main #awn
# deb-src [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) lucid main #awn
# deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) lucid main #compiz
# deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) lucid main #compiz
# deb [http://ppa.launchpad.net/bhavi/ubuntu](http://ppa.launchpad.net/bhavi/ubuntu) lucid main #XSane
# deb-src [http://ppa.launchpad.net/bhavi/ubuntu](http://ppa.launchpad.net/bhavi/ubuntu) lucid main #XSane
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #Google Stable
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free #Google testing
# deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main #Openoffice
# deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) lucid main #Openoffice
deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid free non-free # disabled on upgrade to lucid
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free #Medibuntu
# deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main #Mozilla
# deb-src [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) lucid main #Mozilla
# deb [http://ppa.launchpad.net/zootropo/ppa/ubuntu](http://ppa.launchpad.net/zootropo/ppa/ubuntu) hardy main #zootropo
# deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #Chromium
# deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main #Chromium

I appreciate any help to help solve this problem

---

### Post by andrewthomas on 2010-10-04
Try changing to a different mirror.

---

### Post by neopiper on 2010-10-04
I've tried several mirrors including the main server and it doesn't work.  I'm still getting the error

---

### Post by andrewthomas on 2010-10-04
Get rid of this line
```

deb [http://mirrors.ecvps.com/ubuntu/](http://mirrors.ecvps.com/ubuntu/) lucid free non-free # disabled on upgrade to lucid
```

---

### Post by neopiper on 2010-10-04
AWESOME!!! that solved it..thx a lot

---

### Post by andrewthomas on 2010-10-04
You're welcome.  Glad to be of help.

---

