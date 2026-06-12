---
title: "Error in package managers"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Unkuiri on 2010-04-30
Hi in my notification area there is an error sign and when I try to enter any of the package managers (synaptic or aptitude) it shows this error:

> manuel@manuel-laptop:~$ sudo apt-get update
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-pt_PT                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-pt_PT              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-pt_PT                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-pt_PT                    
Obter:1 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1723B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-pt_PT                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-pt_PT                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-pt_PT              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-pt_PT                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-pt_PT              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-pt_PT            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-pt_PT      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-pt_PT        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-pt_PT      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg                      
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Obter:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-pt_PT                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-pt_PT           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-pt_PT     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-pt_PT       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-pt_PT     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release.gpg                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Translation-pt_PT    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Translation-pt_PT          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Translation-pt_PT    
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-pt_PT            
Obter:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9237B]                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Translation-pt_PT      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/main Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/multiverse Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-backports/universe Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources
Obtidos 9435B em 9s (975B/s)                         
Reading package lists... Error !
E: Read Error - read (5: Data input/output error)
E: The package lists or the status file can't be opened or analised.


Thanks in advance

P.S.:I've updated recently, but I didn't do all updates because if I update to the new kernel I have to do other updates manually (DVB-T) so I intended to wait until the weekend...:(

---

