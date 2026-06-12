---
title: "Problem upgrading from 10.10 to 11.04"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by livij on 2011-05-11
Hi everyone,
I am trying to upgrade from ubuntu 10.10 to 11.04, however I keep getting the following error:
```

W:Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)
```This is the output from sudo apt-get update:
```
jayde@jayde-laptop:~$ sudo apt-get update
[sudo] password for jayde: 
Hit http://au.archive.ubuntu.com maverick Release.gpg                          
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_AU       
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_AU 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://au.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_AU 
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://au.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_AU   
Hit http://au.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com/ubuntu/ karmic/partner Translation-en         
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/partner Translation-en          
Ign http://archive.ubuntu.com/ubuntu/ maverick/partner Translation-en_AU       
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_AU
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_AU
Hit http://au.archive.ubuntu.com karmic-backports Release.gpg                  
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/main Translation-en  
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/restricted Translation-en_AU
Ign http://archive.canonical.com/ubuntu/ karmic/partner Translation-en_AU      
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_AU    
Hit http://archive.canonical.com karmic Release                                
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/universe Translation-en
Hit http://archive.ubuntu.com maverick Release                                 
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_AU           
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_AU
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_AU
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://au.archive.ubuntu.com/ubuntu/ karmic-backports/universe Translation-en_AU
Hit http://au.archive.ubuntu.com maverick-backports Release.gpg                
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://au.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_AU
Hit http://au.archive.ubuntu.com maverick Release                              
Hit http://au.archive.ubuntu.com maverick-updates Release                      
Hit http://au.archive.ubuntu.com karmic-backports Release                      
Hit http://au.archive.ubuntu.com maverick-backports Release                    
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Hit http://au.archive.ubuntu.com maverick/main Sources                         
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://au.archive.ubuntu.com maverick/restricted Sources
Hit http://au.archive.ubuntu.com maverick/universe Sources           
Hit http://au.archive.ubuntu.com maverick/multiverse Sources         
Hit http://au.archive.ubuntu.com maverick/main i386 Packages
Hit http://au.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://au.archive.ubuntu.com maverick/universe i386 Packages
Hit http://archive.canonical.com karmic/partner Sources              
Hit http://archive.canonical.com karmic/partner i386 Packages        
Hit http://au.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://au.archive.ubuntu.com maverick-updates/main Sources
Hit http://au.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://au.archive.ubuntu.com maverick-updates/universe Sources
Hit http://au.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://au.archive.ubuntu.com maverick-updates/main i386 Packages 
Hit http://au.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://au.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://au.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://security.ubuntu.com maverick-security/universe Sources    
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://au.archive.ubuntu.com karmic-backports/main Sources
Hit http://au.archive.ubuntu.com karmic-backports/restricted Sources
Hit http://au.archive.ubuntu.com karmic-backports/universe Sources
Hit http://archive.canonical.com maverick/partner Sources
Hit http://archive.canonical.com maverick/partner i386 Packages
Hit http://au.archive.ubuntu.com karmic-backports/multiverse Sources
Hit http://au.archive.ubuntu.com karmic-backports/main i386 Packages
Hit http://au.archive.ubuntu.com karmic-backports/restricted i386 Packages
Hit http://au.archive.ubuntu.com karmic-backports/universe i386 Packages
Hit http://au.archive.ubuntu.com karmic-backports/multiverse i386 Packages
Hit http://au.archive.ubuntu.com maverick-backports/restricted i386 Packages
Hit http://au.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://au.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Hit http://au.archive.ubuntu.com maverick-backports/universe i386 Packages
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick/Release  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
jayde@jayde-laptop:~$ sudo apt-get update
[sudo] password for jayde: 
Hit http://au.archive.ubuntu.com natty Release.gpg                                                                                                                    
Ign http://au.archive.ubuntu.com/ubuntu/ natty/main Translation-en                                                                                                    
Hit http://au.archive.ubuntu.com/ubuntu/ natty/main Translation-en_AU                                                                                                 
Ign http://au.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en                                                                                              
Hit http://au.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en_AU                                                                                           
Ign http://au.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en                                        
Hit http://au.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en_AU                                     
Ign http://au.archive.ubuntu.com/ubuntu/ natty/universe Translation-en                     
Ign http://au.archive.ubuntu.com/ubuntu/ natty/universe Translation-en_AU                                        
Hit http://au.archive.ubuntu.com natty-updates Release.gpg                                                       
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en                                       
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en_AU              
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en           
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en_AU                              
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en                                 
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en_AU                              
Hit http://security.ubuntu.com natty-security Release.gpg                                                        
Ign http://security.ubuntu.com/ubuntu/ natty-security/main Translation-en                                        
Ign http://security.ubuntu.com/ubuntu/ natty-security/main Translation-en_AU               
Hit http://archive.canonical.com natty Release.gpg                                                               
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en                                            
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en_AU                                         
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en             
Ign http://au.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en_AU          
Hit http://au.archive.ubuntu.com natty-backports Release.gpg                               
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/main Translation-en                                     
Hit http://extras.ubuntu.com natty Release.gpg                                                                   
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en                                                   
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en_AU                                                
Hit http://archive.ubuntu.com natty Release.gpg                                                                  
Ign http://archive.ubuntu.com/ubuntu/ natty/partner Translation-en                                               
Ign http://archive.ubuntu.com/ubuntu/ natty/partner Translation-en_AU                                            
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/main Translation-en_AU                                  
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/multiverse Translation-en         
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/multiverse Translation-en_AU                            
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/restricted Translation-en                               
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/restricted Translation-en_AU                            
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/universe Translation-en                                 
Ign http://au.archive.ubuntu.com/ubuntu/ natty-backports/universe Translation-en_AU                              
Hit http://au.archive.ubuntu.com natty Release                                                                   
Hit http://au.archive.ubuntu.com natty-updates Release                                                           
Hit http://au.archive.ubuntu.com natty-backports Release                                                         
Ign http://security.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en                                                        
Ign http://security.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en_AU                               
Ign http://security.ubuntu.com/ubuntu/ natty-security/restricted Translation-en                                  
Ign http://security.ubuntu.com/ubuntu/ natty-security/restricted Translation-en_AU                               
Ign http://security.ubuntu.com/ubuntu/ natty-security/universe Translation-en              
Ign http://security.ubuntu.com/ubuntu/ natty-security/universe Translation-en_AU           
Hit http://archive.canonical.com natty Release                                                                   
Hit http://security.ubuntu.com natty-security Release                                                            
Hit http://extras.ubuntu.com natty Release                                                                       
Hit http://archive.ubuntu.com natty Release                                                                      
Hit http://au.archive.ubuntu.com natty/main Sources                                                              
Hit http://au.archive.ubuntu.com natty/restricted Sources                                  
Hit http://au.archive.ubuntu.com natty/universe Sources              
Hit http://au.archive.ubuntu.com natty/multiverse Sources                                  
Hit http://au.archive.ubuntu.com natty/main i386 Packages                                  
Hit http://au.archive.ubuntu.com natty/restricted i386 Packages                            
Hit http://au.archive.ubuntu.com natty/universe i386 Packages                              
Hit http://au.archive.ubuntu.com natty/multiverse i386 Packages                            
Hit http://au.archive.ubuntu.com natty-updates/main Sources          
Hit http://archive.canonical.com natty/partner Sources               
Hit http://security.ubuntu.com natty-security/main Sources           
Hit http://extras.ubuntu.com natty/main i386 Packages                
Hit http://au.archive.ubuntu.com natty-updates/restricted Sources    
Hit http://au.archive.ubuntu.com natty-updates/universe Sources
Hit http://au.archive.ubuntu.com natty-updates/multiverse Sources
Hit http://au.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://au.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://au.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://au.archive.ubuntu.com natty-updates/multiverse i386 Packages
Hit http://au.archive.ubuntu.com natty-backports/restricted i386 Packages
Hit http://au.archive.ubuntu.com natty-backports/main i386 Packages  
Hit http://au.archive.ubuntu.com natty-backports/multiverse i386 Packages
Hit http://au.archive.ubuntu.com natty-backports/universe i386 Packages
Hit http://archive.canonical.com natty/partner i386 Packages         
Hit http://security.ubuntu.com natty-security/restricted Sources
Hit http://security.ubuntu.com natty-security/universe Sources
Hit http://security.ubuntu.com natty-security/multiverse Sources
Hit http://security.ubuntu.com natty-security/main i386 Packages
Hit http://security.ubuntu.com natty-security/restricted i386 Packages
Hit http://security.ubuntu.com natty-security/universe i386 Packages
Hit http://security.ubuntu.com natty-security/multiverse i386 Packages
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/natty/Release  Unable to find expected entry  partner/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.
jayde@jayde-laptop:~$ 

```and sources.list:
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://au.archive.ubuntu.com/ubuntu/ natty universe
deb http://au.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://au.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
deb http://au.archive.ubuntu.com/ubuntu/ natty-backports restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner
deb http://archive.ubuntu.com/ubuntu natty partner
deb-src http://archive.ubuntu.com/ubuntu natty partner
```Apologies if there is already a thread for this: I have searched and found nothing.
Any suggestions appreciated. Thanks in advance!

---

### Post by mörgæs on 2011-05-11
Hi, welcome to the fora.

Your machine contains a mix of the Ubuntu versions 9.10 to 11.04. After so many upgrades a fresh install is due.

---

### Post by livij on 2011-05-11
I feared this might be the case.

Thanks very much!

---

### Post by livij on 2011-05-11
I have a new problem now. It seems my computer did a partial upgrade. When I restarted it there are no graphics, just a command line.
Does this mean there are packages missing and a clean install is still necessary, or simply my third party graphics driver (nvidia) has been uninstalled and reinstalling might fix the issue?

Upon starting "welcome to ubuntu 11.04" appears before the command line.

---

### Post by mörgæs on 2011-05-12
Never do a partial upgrade:
[http://ubuntuforums.org/showthread.php?t=1751299](http://ubuntuforums.org/showthread.php?t=1751299)

You shouldn't pay too much attention to the existing installation. Just back up your files and give your poor machine a new one.

---

