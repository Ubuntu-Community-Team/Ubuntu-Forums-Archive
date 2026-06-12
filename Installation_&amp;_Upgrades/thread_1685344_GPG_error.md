---
title: "GPG error"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by leeb9972 on 2011-02-10
Hi, Hoping someone can help me
I get the following error when i sudo apt-get update:

```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)

```

I cant find this on Software Sources, any ideas?

Noticed other posts showing this information:
leeb9972@g33k:~$ sudo apt-get update
[sudo] password for leeb9972: 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                    
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_GB                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                                                                  
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en                  
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_GB                                                  
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_GB                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                                                                     
Ign [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/) maverick/main Translation-en_GB               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                                                             
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_GB                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                                                                    
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                                                       
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en                                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en                                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                                                              
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) maverick/main Translation-en_GB                                       
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_GB                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en                                                
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) maverick/main Translation-en                                  
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_GB                                             
Ign [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/) maverick/main Translation-en_GB                               
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/free Translation-en_GB                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                                                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en                                            
Ign [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/) maverick/main Translation-en                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_GB                                         
Ign [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/) maverick/main Translation-en_GB                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_GB                                   
Ign [http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/](http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/) maverick/main Translation-en                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                                      
Ign [http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/](http://ppa.launchpad.net/freetuxtv/freetuxtv/ubuntu/) maverick/main Translation-en_GB                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_GB                                   
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release.gpg                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                                        
Ign [http://apt.boxee.tv](http://apt.boxee.tv) maverick Release.gpg                                                                          
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic/non-free Translation-en_GB                                                  
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]                                                                  
Ign [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/) maverick/main Translation-en                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_GB                                     
Ign [http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/](http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/) maverick/main Translation-en_GB                      
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg                                                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en                                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                                                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_GB                                       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en                                                 
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) maverick/contrib Translation-en                                 
Ign [http://apt.boxee.tv/](http://apt.boxee.tv/) maverick/main Translation-en                                                                 
Ign [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/) maverick/main Translation-en                              
Ign [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu/) maverick/main Translation-en_GB                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en                                                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en                                    
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en_GB                                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_GB                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en                                    
Ign [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/) maverick/main Translation-en                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_GB                                 
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) maverick/contrib Translation-en_GB                              
Ign [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu/) maverick/main Translation-en_GB                        
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_GB                                                    
Ign [http://apt.boxee.tv/](http://apt.boxee.tv/) maverick/main Translation-en_GB                                                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en                                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_GB                                   
Ign [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/) maverick/main Translation-en                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg                                                           
Ign [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/) maverick/main Translation-en_GB                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                           
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_GB                                        
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release                                                                         
Ign [http://apt.boxee.tv](http://apt.boxee.tv) maverick Release                                                                              
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick Release                                                                   
Ign [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) maverick/main Translation-en_GB                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_GB                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                     
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_GB                                                
Ign [http://ppa.launchpad.net/loneowais/ppa/ubuntu/](http://ppa.launchpad.net/loneowais/ppa/ubuntu/) maverick/main Translation-en                                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_GB                                  
Ign [http://ppa.launchpad.net/loneowais/ppa/ubuntu/](http://ppa.launchpad.net/loneowais/ppa/ubuntu/) maverick/main Translation-en_GB                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_GB                                    
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en                                       
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg [198B]                                                  
Ign [http://apt.boxee.tv](http://apt.boxee.tv) maverick/main i386 Packages/DiffIndex                                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                                                                      
Ign [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) maverick/main Translation-en_GB                                    
Hit [http://download.virtualbox.org](http://download.virtualbox.org) maverick/contrib i386 Packages                                                     
Hit [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main i386 Packages                                                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en                                           
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]                                                            
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_GB                                        
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en                                     
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en_GB                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release                                                                    
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_GB                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en                                     
Hit [http://apt.boxee.tv](http://apt.boxee.tv) maverick/main i386 Packages                                                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                                                                     
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_GB                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free i386 Packages                                                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_GB                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                                                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release                                                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free i386 Packages                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release                                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release [31.4kB]                                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Sources                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources                                                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Sources                                                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources                                                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages                                                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free i386 Packages                                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages                                                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources                                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free i386 Packages                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources                                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release.gpg                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages                  
Ign [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/) maverick/main Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                         
Ign [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/) maverick/main Translation-en_GB           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages [29.0kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                                                         
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages [17.7kB]                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources/DiffIndex                                                     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages/DiffIndex                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Ign [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/) maverick/main Translation-en
Ign [http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/](http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/) maverick/main Translation-en_GB
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release                 
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick Release                 
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick/main Sources                               
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick/main i386 Packages
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick/main Sources
Hit [http://ppa.quickbuild.pearsoncomputing.net](http://ppa.quickbuild.pearsoncomputing.net) maverick/main i386 Packages
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_GB                                              
Get:9 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                  
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en                                                    
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/non-free Translation-en_GB                                                 
Get:10 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                                                                   
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                                                                   
Get:12 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,080B]                                                        
Get:13 [http://dl.google.com](http://dl.google.com) stable/non-free i386 Packages [1,010B]                                                    
Fetched 86.1kB in 12s (7,010B/s)                                                                                      
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)
leeb9972@g33k:~$ 


Thank you

---

### Post by dabl on 2011-02-10
From Google to you:

[http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error](http://en.kioskea.net/faq/809-debian-apt-get-no-pubkey-gpg-error)

---

### Post by leeb9972 on 2011-02-10
Nope still got the error...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)

---

### Post by plucky on 2011-02-10
Post your sources.list and sources.list.d from a terminal (copy & Paste)```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

The complete output please.

Good Luck

---

### Post by BACbOK on 2011-02-10
> **leeb9972 said:**
> Nope still got the error...

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA

You need put in console:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
```

---

### Post by leeb9972 on 2011-02-11
> **BACbOK said:**
> You need put in console:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
```

Great! thanks it worked, thanks to everyone with assistance :)

---

