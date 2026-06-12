---
title: "why are there 'unselectable' updates in the update manager?"
date: 2011-11-06
forum: Installation &amp; Upgrades
---

### Post by andres.ordonez on 2011-11-06
Hi, since some weeks ago there are three updates in the update manager that I can't select. The updates are:

bibliographic-database
Evolution RSS Reader Plugin
Boost.Python Library development files (default version)

Why can't I select them?

This is not a big problem, but I guess there's something wrong with the update manager. Thanks for the help!

I'm using ubuntu 11.10.

---

### Post by Rubi1200 on 2011-11-06
Hi,
please post the output of the following commands:

```
cat /etc/apt/sources.list

sudo apt-get update
```

---

### Post by andres.ordonez on 2011-11-06
```
andres@andres-laptop:~$ cat /etc/apt/sources.list
# added by the release upgrader
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110426)]/ natty main restricted
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://co.archive.ubuntu.com/ubuntu/](http://co.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main #Third party developers repository
# deb [ftp://gfifdev.udea.edu.co/pub/gfifdeb/debian/](ftp://gfifdev.udea.edu.co/pub/gfifdeb/debian/) sid contrib # disabled on upgrade to natty

andres@andres-laptop:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                                                                  
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                         
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [469 B]                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                                                                  
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                               
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                                                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main amd64 Packages                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted amd64 Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe amd64 Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse amd64 Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en_GB         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en_GB   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
Fetched 2,469 B in 4s (597 B/s)
Reading package lists... Done
```

---

