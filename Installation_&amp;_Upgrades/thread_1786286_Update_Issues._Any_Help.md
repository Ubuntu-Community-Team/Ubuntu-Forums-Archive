---
title: "Update Issues. Any Help?"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by meloade on 2011-06-19
I've been having troubles lately getting updates on my computer. Every time I try to update I get the same result.

E: Unable to locate package update

Right now I'm staying in a hotel so I'm not sure if it's just that those servers might be blocked or because of the excruciatingly slow internet speeds but I have some other information if you need it or if it might help.

david@david-davtop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main
# deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) edgy main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe


david@david-davtop:~$ sudo apt-get update
[sudo] password for david: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports InRelease                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy Release.gpg                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy/main i386 Packages/DiffIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release.gpg                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy/main TranslationIndex                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://debian.websterwood.com](http://debian.websterwood.com) edgy/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports Release                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main i386 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse i386 Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main TranslationIndex      
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy/main Translation-en_GB                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe TranslationIndex  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse i386 Packages       
Ign [http://debian.websterwood.com](http://debian.websterwood.com) edgy/main Translation-en                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe i386 Packages         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse TranslationIndex    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted TranslationIndex    
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en_GB            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe TranslationIndex      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_GB                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_GB            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_GB            
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Translation-en               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_GB              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_GB          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_GB    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_GB      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en_GB     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/main Translation-en        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en_GB
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/multiverse Translation-en  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en_GB
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/restricted Translation-en  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en_GB 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-backports/universe Translation-en    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en_GB         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/main Translation-en            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en_GB   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/multiverse Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en_GB   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/restricted Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en_GB     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-proposed/universe Translation-en        
Fetched 2,000 B in 10s (187 B/s)                                               
Reading package lists... Done


Thanks in advance for any help you may give in this problem!

---

### Post by jerrrys on 2011-06-20
why do you have maverick and edgy repositories in your sources?  i think these need to be commented (##) out.

---

