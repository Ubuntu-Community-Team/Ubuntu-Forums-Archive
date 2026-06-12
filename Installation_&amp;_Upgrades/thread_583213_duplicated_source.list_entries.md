---
title: "duplicated source.list entries"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Chris11 on 2007-10-20
SInce upgrading to Gusty I get during every update the error message

> W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-i386_Packages)

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-es (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_universe_i18n_Translation-es)

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_restricted_binary-i386_Packages)

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_main_binary-i386_Packages)

W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy-backports_universe_binary-i386_Packages)

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_gutsy-security_universe_binary-i386_Packages)

I checked at /var/lib/apt/lists/... for duplicated entries with no luck.

Mi sources.list looks like that

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main universe

## Skype
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

## Subtitle editor
deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse

Chris

---

### Post by Stemp on 2007-10-20
There is duplicated lines ;)

By example :
```
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted **universe** multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security **universe**
```

BTW is it all your sources.list ? 
I only see universe for the gutsy repo. no main.

```
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
```

---

### Post by Chris11 on 2007-10-20
Thanks Stamp

but I don't get you point... anyway I don't understand to much about sources.list.. lol

maybe it could help me to unlock the case if you could post the entry of your sources.list and the content of the /var/lib/apt/list/ folder

I'v got checked main, restricted, universe and multiverse 


Thanks

---

### Post by Stemp on 2007-10-20
Ok ;)

Edit your sources.list and put this :

```
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed main restricted  universe multiverse

## Skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

## Subtitle editor
deb http://repository.debuntu.org/ gutsy multiverse
deb-src http://repository.debuntu.org/ gutsy multiverse
```

---

### Post by Chris11 on 2007-10-20
Ahhh.. thx,, I think now I understand the main restricted universe multiverse issue.. 

Chris

---

### Post by DonovanM11 on 2007-11-04
I have the same problem.

```
donovan@dell:~$ sudo apt-get update
Password:
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]                   
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US                 
Get:2 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Get:3 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US             
Get:4 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US      
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Hit http://archive.canonical.com feisty-commercial Release                     
Get:5 http://www.getautomatix.com feisty Release.gpg [189B]                    
Ign http://www.getautomatix.com feisty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com feisty-updates/universe Translation-en_US     
Hit http://us.archive.ubuntu.com feisty Release                                
Hit http://security.ubuntu.com feisty-security Release                         
Hit http://archive.canonical.com feisty-commercial/main Packages               
Hit http://us.archive.ubuntu.com feisty-updates Release                        
Hit http://www.getautomatix.com feisty Release                                 
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://archive.canonical.com feisty-commercial/main Packages               
Hit http://us.archive.ubuntu.com feisty/main Packages                          
Hit http://us.archive.ubuntu.com feisty/restricted Packages                    
Hit http://us.archive.ubuntu.com feisty/main Sources                           
Hit http://www.getautomatix.com feisty/main Packages                           
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources  
Hit http://us.archive.ubuntu.com feisty/universe Packages   
Hit http://us.archive.ubuntu.com feisty/universe Sources                       
Hit http://us.archive.ubuntu.com feisty/multiverse Packages                    
Hit http://us.archive.ubuntu.com feisty/multiverse Sources                     
Hit http://us.archive.ubuntu.com feisty/universe Packages   
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages             
Hit http://security.ubuntu.com feisty-security/multiverse Sources              
Hit http://security.ubuntu.com feisty-security/universe Packages               
Hit http://us.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-updates/universe Packages
Get:6 http://archive.ubuntu.com feisty-backports Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US
Get:7 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US
Get:8 http://archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://archive.ubuntu.com feisty-backports/restricted Packages             
Hit http://archive.ubuntu.com feisty-backports/universe Packages               
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages             
Hit http://archive.ubuntu.com feisty-updates/universe Packages                 
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages               
Hit http://archive.ubuntu.com feisty-security/main Packages                    
Hit http://archive.ubuntu.com feisty-security/restricted Packages              
Hit http://archive.ubuntu.com feisty-security/universe Packages                
Hit http://archive.ubuntu.com feisty-security/multiverse Packages              
Fetched 8B in 6s (1B/s)                                                        
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com feisty/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com feisty-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_feisty-commercial_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

 when i run "cat /etc/apt/sources.list" I get

```
#
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
```

I have feisty fawn 7.04 and trying to upgrade to gusty gibbons 7.10

---

### Post by Chris11 on 2007-11-05
Back up you source.list (just in case...) and replace it with 

> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty  main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) fesity-proposed main restricted  universe multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

#AUTOMATIX REPOS END



I think that should do it  like in my case...

---

