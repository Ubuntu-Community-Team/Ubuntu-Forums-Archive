---
title: "How can I reset my repositories?"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by twtgd09 on 2011-04-28
Hey, i did something to my repositories, and now whenever i run "sudo apt-get update" i get a bunch of error messages that some repository doesnt work. I have no clue how repositories work, and i just want to reset them, and not need to worry about them again. Can anyone help me rest them to a working default?

---

### Post by KegHead on 2011-04-28
Hi!

Have you been to;

system...admin...update manager...software sources?

also;

try:

suso apt-get update

sudo apt-get upgrade -f

(post if you can)

KegHead

---

### Post by wilee-nilee on 2011-04-28
Post your apt/sources.list, run this command and copy paste the output to code tags in a reply.
cat /etc/apt/sources.list

To get code tags open a reply, click on the **(#)** in the reply panel and paste in between.

---

### Post by twtgd09 on 2011-04-28
here's what i get when i sudo apt-get upgrade


Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick Release.gpg                         
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_US       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en   
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Ign [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) maverick/eyecandy Translation-en     
Ign [http://download.tuxfamily.org/3v1deb/](http://download.tuxfamily.org/3v1deb/) maverick/eyecandy Translation-en_US  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_US           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/dan/ppa/ubuntu/](http://ppa.launchpad.net/dan/ppa/ubuntu/) maverick/main Translation-en      
Ign [http://ppa.launchpad.net/dan/ppa/ubuntu/](http://ppa.launchpad.net/dan/ppa/ubuntu/) maverick/main Translation-en_US   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/jacob/evo230/ubuntu/](http://ppa.launchpad.net/jacob/evo230/ubuntu/) maverick/main Translation-en 
Ign [http://ppa.launchpad.net/jacob/evo230/ubuntu/](http://ppa.launchpad.net/jacob/evo230/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick Release                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,079B]                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy Sources                    
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy i386 Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy Sources                    
  404  Not Found [IP: 88.191.250.18 80]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Err [http://download.tuxfamily.org](http://download.tuxfamily.org) maverick/eyecandy i386 Packages              
  404  Not Found [IP: 88.191.250.18 80]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages       
Fetched 2,623B in 6s (418B/s)                                                  
W: Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/maverick/eyecandy/source/Sources.gz](http://download.tuxfamily.org/3v1deb/dists/maverick/eyecandy/source/Sources.gz)  404  Not Found [IP: 88.191.250.18 80]

W: Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/maverick/eyecandy/binary-i386/Packages.gz](http://download.tuxfamily.org/3v1deb/dists/maverick/eyecandy/binary-i386/Packages.gz)  404  Not Found [IP: 88.191.250.18 80]

W: Failed to fetch [http://ppa.launchpad.net/dan/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/dan/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dan/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/dan/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by twtgd09 on 2011-04-28
here are my sources

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main
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

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) maverick eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) maverick eyecandy

---

### Post by wilee-nilee on 2011-04-28
The highlighted areas can be removed the don't need to be there and I suspect being on the same line even with the # that it is a problem.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted **#Added by software-properties**
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick restricted main
deb-src http://archive.ubuntu.com/ubuntu maverick main multiverse universe **#Added by software-properties**

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates restricted main
deb-src http://archive.ubuntu.com/ubuntu maverick-updates restricted main multiverse universe **#Added by software-properties**

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security restricted main
deb-src http://archive.ubuntu.com/ubuntu maverick-security restricted main multiverse universe **#Added by software-properties**
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb http://download.tuxfamily.org/3v1deb maverick eyecandy
deb-src http://download.tuxfamily.org/3v1deb maverick eyecandy
twtgd09 is offline Report Post   	Reply With Quote
```

So your original question was resetting here is a site that will generate a source list for you be careful, save the one you have in the process, if you do any changes.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

