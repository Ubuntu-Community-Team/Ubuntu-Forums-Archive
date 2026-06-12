---
title: "sources update errors"
date: 2009-11-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-11-10
[SIZE="4"]**Solved**[/SIZE]. It was inside sources.d chrome listing. It didn't start with the "http://ppa" that's what I was searching on. compressed and removed chrome list and all is well. Sorry for this.
For the life of me I can't seem to track down this 404 sources.list error. I looked at "/etc/apt/every file and directory in there", but I still get this "ppa" error. No idea where "**[http://ppa](http://ppa)**..." is coming from.

$ sudo aptitude update

```
Get:1 http://dl.google.com stable Release.gpg [191B]
Ign http://dl.google.com stable/main Translation-en_US                                                                       
Get:2 http://dl.google.com stable Release [1,310B]                                                                           
Hit http://archive.canonical.com lucid Release.gpg                                                                           
Ign http://archive.canonical.com lucid/partner Translation-en_US                                                             
Hit http://security.ubuntu.com lucid-security Release.gpg                                                                    
Ign http://security.ubuntu.com lucid-security/main Translation-en_US                                                         
Ign http://security.ubuntu.com lucid-security/restricted Translation-en_US                                                   
Get:3 http://dl.google.com stable/main Packages [621B]                                                                       
Hit http://us.archive.ubuntu.com lucid Release.gpg                                                                           
Ign http://us.archive.ubuntu.com lucid/main Translation-en_US                                                    
Ign http://us.archive.ubuntu.com lucid/restricted Translation-en_US                                                          
[COLOR="Red"]Ign http://ppa.launchpad.net lucid Release.gpg                                                                   
Ign http://ppa.launchpad.net lucid/main Translation-en_US                                                        
Ign http://ppa.launchpad.net lucid Release.gpg                                                                   
[/COLOR]Hit http://archive.canonical.com lucid Release                                                                   
Hit http://packages.medibuntu.org lucid Release.gpg                                                              
Ign http://packages.medibuntu.org lucid/free Translation-en_US                                                   
Ign http://packages.medibuntu.org lucid/non-free Translation-en_US                                               
Ign http://security.ubuntu.com lucid-security/universe Translation-en_US                                         
Ign http://security.ubuntu.com lucid-security/multiverse Translation-en_US                 
Hit http://security.ubuntu.com lucid-security Release                                                            
Ign http://us.archive.ubuntu.com lucid/universe Translation-en_US                                                
Ign http://us.archive.ubuntu.com lucid/multiverse Translation-en_US                        
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                                 
Ign http://us.archive.ubuntu.com lucid-updates/main Translation-en_US                                            
Ign http://us.archive.ubuntu.com lucid-updates/restricted Translation-en_US                                      
Ign http://us.archive.ubuntu.com lucid-updates/universe Translation-en_US                                        
Ign http://us.archive.ubuntu.com lucid-updates/multiverse Translation-en_US                                      
[COLOR="red"]Ign http://ppa.launchpad.net lucid/main Translation-en_US                                                        
[/COLOR]Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                                                     
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US                                          
[COLOR="red"]Ign http://ppa.launchpad.net lucid Release                                                                       
[/COLOR]Hit http://archive.canonical.com lucid/partner Packages                                                          
Hit http://packages.medibuntu.org lucid Release                                                                  
Hit http://security.ubuntu.com lucid-security/main Packages                                                    
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US              
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US                
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US                                    
Hit http://us.archive.ubuntu.com lucid Release                                                                   
Hit http://us.archive.ubuntu.com lucid-updates Release                                                                       
Ign http://ppa.launchpad.net lucid Release                                                                                   
Hit http://archive.canonical.com lucid/partner Sources                                                                       
Hit http://packages.medibuntu.org lucid/free Packages                                                            
Hit http://security.ubuntu.com lucid-security/restricted Packages                          
Hit http://security.ubuntu.com lucid-security/main Sources                                 
Hit http://security.ubuntu.com lucid-security/restricted Sources                           
Hit http://security.ubuntu.com lucid-security/universe Packages                            
Hit http://us.archive.ubuntu.com lucid-backports Release                                   
[COLOR="red"]Ign http://ppa.launchpad.net lucid/main Packages                                                                
[/COLOR]Hit http://packages.medibuntu.org lucid/non-free Packages                                  
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
[COLOR="red"]Ign http://ppa.launchpad.net lucid/main Packages
[/COLOR]Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources
[COLOR="red"]Ign http://ppa.launchpad.net lucid/main Packages
[/COLOR]Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources
[COLOR="red"]Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
[/COLOR]Fetched 2,122B in 2s (746B/s)
Reading package lists... Done

```

Here is my sources.list
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Alpha i386 (20090722.2)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

---

