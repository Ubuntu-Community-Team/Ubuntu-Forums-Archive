---
title: "Jaunty Sources List"
date: 2008-11-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2008-11-30
Would any one care to share a nice 'complete' Jaunty sources list.
Some how I think I may be missing some thing and would like to compare.
When I upgraded, I used a sources list that was provided in one of the first few threads regarding Jaunty and commented out my Intrepid. I almost want to go back and edit the Intrepid list but there was so much added (ppa's and such)junk.
Thanks

---

### Post by danf_1979 on 2008-11-30
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe                      
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe                  
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe              
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe          

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse                     
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse                 
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse             
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse         

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
# deb http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://cl.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
# deb http://archive.canonical.com/ubuntu jaunty partner                 
# deb-src http://archive.canonical.com/ubuntu jaunty partner             

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe           
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe       
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse         
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse     

```

---

### Post by ccw on 2008-11-30
> **DougieFresh4U said:**
> Would any one care to share a nice 'complete' Jaunty sources list.
Some how I think I may be missing some thing and would like to compare.
When I upgraded, I used a sources list that was provided in one of the first few threads regarding Jaunty and commented out my Intrepid. I almost want to go back and edit the Intrepid list but there was so much added (ppa's and such)junk.
Thanks

This is mine (I'll remove the intrepid repos in about a month)... 

```
#8.10 Intrepid Ibex
deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-proposed main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse

#9.04 Jaunty Jackalope
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu jaunty-security main restricted universe multiverse

#Medibuntu Jaunty
deb http://packages.medibuntu.org/ jaunty free non-free
```

---

### Post by autocrosser on 2008-11-30
You need to keep Intrepid in medibuntu-they have not setup a Jaunty source yet....

My list looks like:

#Jaunty Sources

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed main restricted multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted multiverse universe

#Added Intrepid stuff until Jaunty gets going

#Uncomment the following two lines to add software from Canonical's
#'partner' repository. This software is not part of Ubuntu, but is
#offered by Canonical and the respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# PulseAudio Fixes - [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

#Medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free

#Nano Archive
# deb [http://www.nanolx.org/apt/](http://www.nanolx.org/apt/) excelsior main  <<<<<<<<<<<<<<extra themes & fun stuff

#extra stuff
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb [http://ppa.launchpad.net/usplash-smooth/ubuntu](http://ppa.launchpad.net/usplash-smooth/ubuntu) intrepid main   <<<<<<<<<<<<<<<progressive bar for usplash
deb-src [http://ppa.launchpad.net/usplash-smooth/ubuntu](http://ppa.launchpad.net/usplash-smooth/ubuntu) intrepid main
deb [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main  <<<<<<<<<<<<<<<<<Ralink wireless drivers--not for the .28 kernel yet
deb-src [http://ppa.launchpad.net/stgraber/ubuntu](http://ppa.launchpad.net/stgraber/ubuntu) intrepid main
#deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main   <<<<<<<<<<<restricted PPA for .28 kernel
#deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main

---

