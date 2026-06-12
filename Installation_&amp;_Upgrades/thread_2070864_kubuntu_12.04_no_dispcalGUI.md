---
title: "kubuntu 12.04 no dispcalGUI"
date: 2012-10-13
forum: Installation &amp; Upgrades
---

### Post by josvanr on 2012-10-13
I upgraded from kubuntu 11.x to 12.04 now I can't find dispcalGUI anymore. Did they just throw that out or am I doing somehthing wrong?

josvanr

---

### Post by oldos2er on 2012-10-14
It's in the universe repository: ```
sudo apt-get update && sudo apt-get install dispcalgui
```

---

### Post by josvanr on 2012-10-14
Thnx but it no seeme to work

I added both universe and multiverse to software sources in muon (already had that) and I also tried to switch to a different server.
Also I tried lower and upper case (because the binary is called dispcalGUI). I also can't find it in muon 'search'.... Are you using it yourself in 12.04 ?

Josvanr



jos@bugix:~$ sudo apt-get update && sudo apt-get install dispcalgui
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise InRelease
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates InRelease                                                  
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports InRelease                                                                       
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security InRelease                                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release.gpg                                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release.gpg                                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release.gpg                                                                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security Release.gpg                                                                      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release                                                                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release                                                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release                                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security Release                                                                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Sources                                                                                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Sources                                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Sources                                                                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Sources                                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main i386 Packages                                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted i386 Packages                                                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe i386 Packages                                                                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse i386 Packages                                                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main TranslationIndex                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse TranslationIndex                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted TranslationIndex                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe TranslationIndex                                                                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Sources                                                                      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Sources                                                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Sources                                                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Sources                                                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main i386 Packages                                                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted i386 Packages                                                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe i386 Packages                                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse i386 Packages                                                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main TranslationIndex                                                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe TranslationIndex                                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Sources                                                                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Sources                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Sources                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Sources                                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main i386 Packages                                                              
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted i386 Packages                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse i386 Packages                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe i386 Packages                                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main TranslationIndex                                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe TranslationIndex                                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main Sources                                                                     
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted Sources                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe Sources                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse Sources                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main i386 Packages                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted i386 Packages                                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe i386 Packages                                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse i386 Packages                                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main TranslationIndex                                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse TranslationIndex                                                      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted TranslationIndex                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe TranslationIndex                                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Translation-en                                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Translation-en                                                                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Translation-en                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Translation-en                                                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Translation-en                                                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Translation-en                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Translation-en                                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Translation-en                                                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Translation-en                                                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Translation-en                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Translation-en                                                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Translation-en                                                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main Translation-en                                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse Translation-en                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted Translation-en                                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe Translation-en                                                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                                                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dispcalgui
jos@bugix:~$ sudo apt-get update && sudo apt-get install dispcalGUI
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise InRelease
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates InRelease          
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports InRelease                               
Ign [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security InRelease                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release.gpg                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release.gpg         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release.gpg       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security Release.gpg        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise Release                                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security Release            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Sources                                                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Sources                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Sources            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Sources          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main i386 Packages                                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted i386 Packages                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe i386 Packages                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse i386 Packages                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main TranslationIndex                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse TranslationIndex                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted TranslationIndex                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe TranslationIndex                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Sources                              
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Sources                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Sources                          
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Sources                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main i386 Packages                        
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe i386 Packages                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse i386 Packages                  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted TranslationIndex               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe TranslationIndex                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Sources                            
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Sources                      
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Sources  
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main Sources                             
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted Sources                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe Sources   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse Sources 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main i386 Packages 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse i386 Packages                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main TranslationIndex                    
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/main Translation-en                               
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/multiverse Translation-en                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/restricted Translation-en                         
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise/universe Translation-en                           
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/main Translation-en                       
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-backports/universe Translation-en                 
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/main Translation-en                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US   
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/restricted Translation-en                
Hit [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) precise-security/universe Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dispcalGUI

jos@bugix:~$

---

### Post by josvanr on 2012-10-14
ps: 

jos@bugix:~$ cat /etc/apt/sources.list
# deb cdrom:[Kubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted                                                                                                            
                                                                                                                                                                                                                 
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to                                                                                                                                        
# newer versions of the distribution.                                                                                                                                                                            
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise main restricted universe                                                                                                                                        
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise main restricted universe                                                                                                                                    
                                                                                                                                                                                                                 
## Major bug fix updates produced after the final release of the                                                                                                                                                 
## distribution.                                                                                                                                                                                                 
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe                                                                                                                                
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe                                                                                                                            
                                                                                                                                                                                                                 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu                                                                                                                                      
## team. Also, please note that software in universe WILL NOT receive any                                                                                                                                        
## review or updates from the Ubuntu security team.                                                                                                                                                              
                                                                                                                                                                                                                 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu                                                                                                                                      
## team, and may not be under a free licence. Please satisfy yourself as to                                                                                                                                      
## your rights to use the software. Also, please note that software in                                                                                                                                           
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-backports main restricted multiverse universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-backports main restricted multiverse universe

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-security main restricted universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-security main restricted universe
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-security multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
jos@bugix:~$

---

### Post by oldos2er on 2012-10-14
I'm actually using 12.10. You're right though, it doesn't seem to exist for any version except 12.10 now: [http://packages.ubuntu.com/search?keywords=dispcalgui&searchon=all&suite=all&section=all](http://packages.ubuntu.com/search?keywords=dispcalgui&searchon=all&suite=all&section=all)

---

