---
title: "sudo apt-get update error"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by kurniawanz on 2011-02-04
yesterday i install mastersys,but i uninstall again and i remove the repository of mastersys
the problem is after i uninstall that application if i type sudo apt-get update in terminal appear like this


root@kurniawan-HP-Pavilion-dv2-Notebook-PC:/home/kurniawan# sudo apt-get update
Ign file: maverick Release.gpg
Ign file:///opt/locrepo/repository/ maverick/main Translation-en    
Ign file:///opt/locrepo/repository/ maverick/main Translation-en_US 
Ign file:///opt/locrepo/repository/ maverick/multiverse Translation-en
Ign file:///opt/locrepo/repository/ maverick/multiverse Translation-en_US
Ign file:///opt/locrepo/repository/ maverick/restricted Translation-en
Ign file:///opt/locrepo/repository/ maverick/restricted Translation-en_US
Ign file:///opt/locrepo/repository/ maverick/universe Translation-en 
Ign file:///opt/locrepo/repository/ maverick/universe Translation-en_US        
Get:1 file: maverick Release [11.0kB]                                          
Ign file: maverick/main i386 Packages/DiffIndex                                
Ign file: maverick/restricted i386 Packages/DiffIndex                          
Ign file: maverick/multiverse i386 Packages/DiffIndex                          
Ign file: maverick/universe i386 Packages/DiffIndex                            
Ign file: maverick/main i386 Packages                                          
Ign file: maverick/restricted i386 Packages                                    
Ign file: maverick/multiverse i386 Packages                                    
Ign file: maverick/universe i386 Packages                                      
Ign file: maverick/main i386 Packages                                          
Ign file: maverick/restricted i386 Packages                                    
Ign file: maverick/multiverse i386 Packages                                    
Ign file: maverick/universe i386 Packages                                      
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                           
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick Release.gpg                               
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/main Translation-en               
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/main Translation-en_US            
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/multiverse Translation-en         
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/multiverse Translation-en_US      
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/restricted Translation-en         
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/restricted Translation-en_US      
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/universe Translation-en           
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick/universe Translation-en_US        
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/bean123ch/burg/ubuntu/](http://ppa.launchpad.net/bean123ch/burg/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/bean123ch/burg/ubuntu/](http://ppa.launchpad.net/bean123ch/burg/ubuntu/) maverick/main Translation-en_US
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security Release.gpg                      
Hit [http://hacktolive.org](http://hacktolive.org) maverick Release.gpg                                 
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/main Translation-en
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/main Translation-en_US
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates Release.gpg                       
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/main Translation-en       
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/](http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/restricted Translation-en 
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/universe Translation-en   
Ign [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick Release                                   
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/multiverse Translation-en    
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/multiverse Translation-en_US 
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/partner Translation-en       
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/partner Translation-en_US    
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/restricted Translation-en    
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/restricted Translation-en_US 
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/universe Translation-en
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en
Ign [http://hacktolive.org/repo/maverick/](http://hacktolive.org/repo/maverick/) maverick/universe Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release             
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security Release                          
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                    
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates Release                           
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://hacktolive.org](http://hacktolive.org) maverick Release                                     
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/main Sources                              
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/universe Sources                
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/restricted Sources              
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/multiverse Sources              
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/universe i386 Packages                    
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/restricted i386 Packages        
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick/multiverse i386 Packages        
Ign [http://hacktolive.org](http://hacktolive.org) maverick/main i386 Packages                          
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security/universe Sources                 
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security/main Sources                     
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security/multiverse Sources               
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-security/restricted Sources     
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/universe Sources        
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/main Sources                      
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/multiverse Sources                
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/restricted Sources      
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/universe i386 Packages  
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/main i386 Packages      
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/multiverse i386 Packages
Hit [http://kambing.ui.ac.id](http://kambing.ui.ac.id) maverick-updates/restricted i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                        
Ign [http://hacktolive.org](http://hacktolive.org) maverick/restricted i386 Packages          
Ign [http://hacktolive.org](http://hacktolive.org) maverick/multiverse i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/universe i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/partner i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Ign [http://hacktolive.org](http://hacktolive.org) maverick/main i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/restricted i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/multiverse i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/universe i386 Packages
Ign [http://hacktolive.org](http://hacktolive.org) maverick/partner i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) maverick/main i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) maverick/restricted i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) maverick/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) maverick/universe i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) maverick/partner i386 Packages                       
Fetched 2,733B in 6s (425B/s)                                                  
W: Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


what happened and how to resolve it

thanks :)

---

### Post by Kirboosy on 2011-02-04
Apparently that source has died? I'm guessing...

You could go under your Software Sources and disable that repository. (System-->Admin-->Software Sources)

---

### Post by kurniawanz on 2011-02-04
i've been delete sources for remastersys,but still like that if update

---

### Post by Kirboosy on 2011-02-04
I don't think the one thats failing is related to the remastersys repository. I could be wrong though.

---

