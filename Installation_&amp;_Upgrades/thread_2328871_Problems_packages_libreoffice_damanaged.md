---
title: "Problems packages libreoffice damanaged"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by zlatan81 on 2016-06-25
Good morning
I've a problem with packages of libreoffice. I see it with the command sudo apt-get check
I've try with sudo apt-get -f install but without success.
Please help me because I can't install or update anything.

[ATTACH=CONFIG]269769[/ATTACH] 

Thank you

---

### Post by vasa1 on 2016-06-25
Please post the output of
```
LANG=C sudo apt-get update
```and
```
LANG=C sudo apt-get upgrade
```

And please enclose the contents within code tags like this: [noparse]```
terminal output goes here
```[/noparse]

---

### Post by zlatan81 on 2016-06-25
output UPDATE:

```
claudio@claudio:~$ sudo apt-get update
[sudo] password for claudio: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Trovato [http://dl.google.com](http://dl.google.com) stable Release.gpg                                
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                            
Trovato [http://dl.google.com](http://dl.google.com) stable Release                                    
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                           
Trovato [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-it_IT                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-it                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Trovato [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                            
Scaricamento di:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease [65,9 kB] 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                        
Trovato [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages                   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.canonical.com](http://archive.canonical.com) trusty Release                            
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security InRelease                    
Trovato [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Scaricamento di:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed InRelease [65,9 kB]
Trovato [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease                   
Trovato [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty Release.gpg                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME InRelease                               
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty Release                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Ign [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 InRelease                             
Scaricamento di:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources [277 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Scaricamento di:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources [5.352 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Scaricamento di:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources [157 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty InRelease                                  
Scaricamento di:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources [5.936 B]
Scaricamento di:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages [748 kB]
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                           
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-it_IT                   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-it                      
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Scaricamento di:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages [15,6 kB]
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en                      
Scaricamento di:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15,5 kB]          
Scaricamento di:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages [363 kB]
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main i386 Packages                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Scaricamento di:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13,6 kB]
Err [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main i386 Packages                     
  404  Not Found
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en           
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main Translation-it_IT                 
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main Translation-it                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Ign [http://repo.mate-desktop.org](http://repo.mate-desktop.org) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-it_IT            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en       
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Sources                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Sources             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Sources           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Sources           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main i386 Packages           
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-it               
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe i386 Packages       
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                              
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted i386 Packages     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse i386 Packages
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/main Translation-en          
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/multiverse Translation-en    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/restricted Translation-en    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2/main Translation-en               
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-security/universe Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Scaricamento di:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/main i386 Packages [125 kB]
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Scaricamento di:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [28 B]
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Scaricamento di:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/universe i386 Packages [18,7 kB]
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Scaricamento di:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/restricted i386 Packages [28 B]
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/main Translation-en          
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/multiverse Translation-en    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/restricted Translation-en    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-proposed/universe Translation-en      
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages      
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en         
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME Release.gpg                             
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME Release                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources                          
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources                      
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources              
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages              
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages              
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-it                   
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en            
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-it             
Scaricamento di:16 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources [17,6 kB]      
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en             
Scaricamento di:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [20,4 kB]
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-it             
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en             
Scaricamento di:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [10,8 kB]
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-it        
Trovato [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en        
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                      
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-it_IT                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-it_IT              
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-it_IT              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-it_IT                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME/main Sources                            
  404  Not Found [IP: 91.189.88.152 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME/main i386 Packages                      
  404  Not Found [IP: 91.189.88.152 80]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME/main Translation-it_IT                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME/main Translation-it               
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) CODENAME/main Translation-en                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                    
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                           
Trovato [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                     
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it_IT
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-it
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Recuperati 1.925 kB in 29s (65,5 kB/s)
W: Non è disponibile alcuna chiave pubblica per i seguenti ID di chiavi:
1397BC53640DB551
W: Impossibile recuperare [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Impossibile trovare la voce "main/binary-i386/Packages" nel file Release (voce in sources.list errata o file danneggiato)

W: Impossibile recuperare [http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/trusty/main/binary-i386/Packages](http://repo.mate-desktop.org/archive/1.8/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Impossibile recuperare [http://archive.ubuntu.com/ubuntu/dists/CODENAME/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/CODENAME/main/source/Sources)  404  Not Found [IP: 91.189.88.152 80]

W: Impossibile recuperare [http://archive.ubuntu.com/ubuntu/dists/CODENAME/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/CODENAME/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.152 80]

W: Impossibile recuperare [http://ppa.launchpad.net/atareao/updf/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/atareao/updf/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/atareao/updf/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/atareao/updf/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gma500/emgd/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/gma500/emgd/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gma500/emgd/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gma500/emgd/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gnomebaker/stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gpoweroff/stable/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/gpoweroff/stable/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Impossibile recuperare [http://ppa.launchpad.net/gpoweroff/stable/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/gpoweroff/stable/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
```

---

### Post by zlatan81 on 2016-06-25
outoput UPGRADE:

claudio@claudio:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_multiverse_binary-i386_Packages)
W: È consigliato eseguire "apt-get update" per correggere questi problemi
E: Dipendenze non trovate. Riprovare usando -f.

---

### Post by grahammechanical on 2016-06-25
First you need to disable some PPAs. All those PPAs listed as "impossibile recuparare" should be disabled. They are causing update problems that are not related to your problem with Libreoffice.

You also need to re-install Libreoffice.

Regards.

---

### Post by zlatan81 on 2016-06-25
> **grahammechanical said:**
> First you need to disable some PPAs. All those PPAs listed as "impossibile recuparare" should be disabled. They are causing update problems that are not related to your problem with Libreoffice.

You also need to re-install Libreoffice.

Regards.

About the new update, now there aren't errors :)
```

claudio@claudio:~$ sudo apt-get update
[sudo] password for claudio: 
Ign http://archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates InRelease                     
Trovato http://deb.playonlinux.com trusty InRelease                            
Scaricamento di:1 http://extras.ubuntu.com trusty Release.gpg [72 B]           
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security InRelease                    
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://archive.canonical.com trusty Release                            
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-proposed InRelease                    
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://extras.ubuntu.com trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports InRelease                   
Trovato http://archive.canonical.com trusty/partner Sources                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/main Sources                  
Trovato http://archive.canonical.com trusty/partner Translation-en             
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/restricted Sources            
Trovato http://archive.ubuntu.com trusty-updates/universe Sources              
Ign http://ppa.launchpad.net jaunty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/multiverse Sources            
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Trovato http://archive.ubuntu.com trusty-updates/main i386 Packages            
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/restricted i386 Packages      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe i386 Packages        
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/multiverse i386 Packages      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/main Translation-en           
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release.gpg                       
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe Translation-en       
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/main Sources                 
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Trovato http://download.ebz.epson.net lsb3.2 Release                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/universe Sources             
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://archive.ubuntu.com trusty-security/restricted Sources           
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Trovato http://archive.ubuntu.com trusty-security/multiverse Sources           
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Trovato http://archive.ubuntu.com trusty-security/main i386 Packages           
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/universe i386 Packages       
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/restricted i386 Packages     
Trovato http://download.ebz.epson.net lsb3.2/main i386 Packages                
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/multiverse i386 Packages     
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-security/universe Translation-en      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it_IT            
Trovato http://archive.ubuntu.com trusty-proposed/main i386 Packages           
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-proposed/universe i386 Packages       
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-proposed/restricted i386 Packages     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-proposed/main Translation-en          
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-proposed/multiverse Translation-en    
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/universe Translation-en      
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/multiverse i386 Packages    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/main i386 Packages          
Trovato http://archive.ubuntu.com trusty-backports/restricted i386 Packages    
Trovato http://archive.ubuntu.com trusty-backports/universe i386 Packages      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/main Translation-en         
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://ppa.launchpad.net jaunty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/universe Translation-en     
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty/main Sources 
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://archive.ubuntu.com trusty/universe Sources                
Trovato http://ppa.launchpad.net trusty/main i386 Packages               
Trovato http://download.ebz.epson.net lsb3.2/main Translation-en         
Trovato http://archive.ubuntu.com trusty/multiverse Sources              
Trovato http://ppa.launchpad.net trusty/main Translation-en              
Trovato http://archive.ubuntu.com trusty/main i386 Packages              
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages              
Trovato http://archive.ubuntu.com trusty/universe i386 Packages         
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://archive.ubuntu.com trusty/main Translation-it
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/restricted Translation-it
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com trusty/restricted Translation-en
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/universe Translation-it
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com trusty/universe Translation-en
Trovato http://ppa.launchpad.net trusty/main Translation-en             
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty Release.gpg
Trovato http://ppa.launchpad.net trusty Release.gpg                        
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources                     
Ign http://archive.ubuntu.com trusty/main Translation-it_IT              
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT        
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT        
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty Release.gpg
Trovato http://ppa.launchpad.net trusty Release
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net jaunty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net jaunty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net jaunty/main Translation-it_IT                     
Ign http://ppa.launchpad.net jaunty/main Translation-it                        
Ign http://ppa.launchpad.net jaunty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Recuperati 72 B in 14s (4 B/s)                                                 
Lettura elenco dei pacchetti... Fatto


```

About the upgrade, there are errors
```
claudio@claudio:~$ sudo apt-get upgrade
[sudo] password for claudio: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.


```

About the re-installation of Libreoffice I used the commands **sudo add-apt-repository ppa:libreoffice/libreoffice-5-1** 
 and[B] sudo apt-get update && sudo apt-get dist-upgrade
[/B]but I've the same errors of the upgrade

```
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html

This ppa will:
- not contain alpha and beta releases like 5.1.0~beta2
- not contain updates to the next major (5.2.x)
- contain minor release updates and their release candidates -- these can be
  considered stable

Note that for minor release updates (5.1.1, 5.1.2, 5.1.3 ...) an rc2 is almost always exactly the same as the final version.

See: https://wiki.documentfoundation.org/ReleasePlan for details,
and: http://www.libreoffice.org/discover/new-features/ and https://wiki.documentfoundation.org/ReleaseNotes/5.1 for new features and fixes.

 Maggiori informazioni: https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-1
Premere [INVIO] per continuare o Ctrl+C per annullare

gpg: portachiavi "/tmp/tmpzkx99o6r/secring.gpg" creato
gpg: portachiavi "/tmp/tmpzkx99o6r/pubring.gpg" creato
gpg: richiesta della chiave 1378B444 dal server hkp keyserver.ubuntu.com
gpg: /tmp/tmpzkx99o6r/trustdb.gpg: creato il trustdb
gpg: chiave 1378B444: chiave pubblica "Launchpad PPA for LibreOffice Packaging" importata
gpg: non è stata trovata alcuna chiave completamente affidabile
gpg: Numero totale esaminato: 1
gpg:               importate: 1  (RSA: 1)
OK
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html

This ppa will:
- not contain alpha and beta releases like 5.1.0~beta2
- not contain updates to the next major (5.2.x)
- contain minor release updates and their release candidates -- these can be
  considered stable

Note that for minor release updates (5.1.1, 5.1.2, 5.1.3 ...) an rc2 is almost always exactly the same as the final version.

See: https://wiki.documentfoundation.org/ReleasePlan for details,
and: http://www.libreoffice.org/discover/new-features/ and https://wiki.documentfoundation.org/ReleaseNotes/5.1 for new features and fixes.

 Maggiori informazioni: https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-1
Premere [INVIO] per continuare o Ctrl+C per annullare

gpg: portachiavi "/tmp/tmpm_665uct/secring.gpg" creato
gpg: portachiavi "/tmp/tmpm_665uct/pubring.gpg" creato
gpg: richiesta della chiave 1378B444 dal server hkp keyserver.ubuntu.com
gpg: /tmp/tmpm_665uct/trustdb.gpg: creato il trustdb
gpg: chiave 1378B444: chiave pubblica "Launchpad PPA for LibreOffice Packaging" importata
gpg: non è stata trovata alcuna chiave completamente affidabile
gpg: Numero totale esaminato: 1
gpg:               importate: 1  (RSA: 1)
OK
claudio@claudio:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://extras.ubuntu.com trusty Release.gpg                            
Trovato http://archive.canonical.com trusty Release                            
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://archive.canonical.com trusty/partner Sources                    
Trovato http://extras.ubuntu.com trusty/main Sources                           
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Trovato http://archive.canonical.com trusty/partner Translation-en             
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://deb.playonlinux.com trusty InRelease                            
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                                 
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:1 http://archive.ubuntu.com trusty-updates InRelease [65,9 kB] 
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security InRelease                    
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:2 http://archive.ubuntu.com trusty-proposed InRelease [65,9 kB]
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-backports InRelease                   
Ign http://ppa.launchpad.net jaunty InRelease                                  
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Scaricamento di:3 http://ppa.launchpad.net trusty InRelease [15,5 kB]          
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Scaricamento di:4 http://archive.ubuntu.com trusty-updates/main Sources [277 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:5 http://archive.ubuntu.com trusty-updates/restricted Sources [5.352 B]
Ign http://ppa.launchpad.net trusty InRelease                                  
Scaricamento di:6 http://archive.ubuntu.com trusty-updates/universe Sources [157 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release.gpg                       
Scaricamento di:7 http://archive.ubuntu.com trusty-updates/multiverse Sources [5.936 B]
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:8 http://archive.ubuntu.com trusty-updates/main i386 Packages [748 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release                           
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Scaricamento di:9 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Scaricamento di:10 http://archive.ubuntu.com trusty-updates/universe i386 Packages [363 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://download.ebz.epson.net lsb3.2/main i386 Packages                
Scaricamento di:11 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13,6 kB]
Trovato http://archive.ubuntu.com trusty-updates/main Translation-en           
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe Translation-en       
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it_IT            
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/main Sources                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/universe Sources             
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/restricted Sources           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-security/multiverse Sources           
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-security/main i386 Packages           
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/universe i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages                
Trovato http://archive.ubuntu.com trusty-security/restricted i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en               
Trovato http://archive.ubuntu.com trusty-security/multiverse i386 Packages     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://download.ebz.epson.net lsb3.2/main Translation-en               
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-security/universe Translation-en      
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Scaricamento di:12 http://archive.ubuntu.com trusty-proposed/main i386 Packages [125 kB]
Trovato http://ppa.launchpad.net trusty/main Sources                           
Scaricamento di:13 http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Scaricamento di:14 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [18,7 kB]
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Scaricamento di:15 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-proposed/main Translation-en          
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/multiverse Translation-en    
Trovato http://ppa.launchpad.net jaunty Release.gpg                            
Scaricamento di:16 http://ppa.launchpad.net trusty/main i386 Packages [29,7 kB]
Trovato http://archive.ubuntu.com trusty-proposed/restricted Translation-en    
Trovato http://archive.ubuntu.com trusty-proposed/universe Translation-en      
Scaricamento di:17 http://ppa.launchpad.net trusty/main Translation-en [11,6 kB]
Trovato http://archive.ubuntu.com trusty-backports/multiverse i386 Packages    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/main i386 Packages          
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/restricted i386 Packages    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/universe i386 Packages      
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/main Translation-en         
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/universe Translation-en     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/main Sources                          
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/universe Sources                      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/multiverse Sources                    
Trovato http://archive.ubuntu.com trusty/main i386 Packages                    
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages              
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/universe i386 Packages                
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages              
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/main Translation-it                   
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/main Translation-en                   
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it             
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en             
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/restricted Translation-it             
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/restricted Translation-en             
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty/universe Translation-it               
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/universe Translation-en               
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Ign http://archive.ubuntu.com trusty/main Translation-it_IT                    
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT              
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT              
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT                
Trovato http://ppa.launchpad.net jaunty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net jaunty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net jaunty/main Translation-it_IT                     
Ign http://ppa.launchpad.net jaunty/main Translation-it                        
Ign http://ppa.launchpad.net jaunty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Recuperati 1.918 kB in 20s (94,3 kB/s)                                         
Lettura elenco dei pacchetti... Fatto
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.


```

---

### Post by zlatan81 on 2016-06-25
> **vasa1 said:**
> Please post the output of
```
LANG=C sudo apt-get update
```and
```
LANG=C sudo apt-get upgrade
```

And please enclose the contents within code tags like this: [noparse]```
terminal output goes here
```[/noparse]


Now about the new update, now there aren't errors :smile:
```

claudio@claudio:~$ sudo apt-get update
[sudo] password for claudio: 
Ign http://archive.ubuntu.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Ign http://archive.canonical.com trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates InRelease                     
Trovato http://deb.playonlinux.com trusty InRelease                            
Scaricamento di:1 http://extras.ubuntu.com trusty Release.gpg [72 B]           
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security InRelease                    
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://archive.canonical.com trusty Release                            
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-proposed InRelease                    
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://extras.ubuntu.com trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports InRelease                   
Trovato http://archive.canonical.com trusty/partner Sources                    
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/main Sources                  
Trovato http://archive.canonical.com trusty/partner Translation-en             
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/restricted Sources            
Trovato http://archive.ubuntu.com trusty-updates/universe Sources              
Ign http://ppa.launchpad.net jaunty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/multiverse Sources            
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Trovato http://archive.ubuntu.com trusty-updates/main i386 Packages            
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/restricted i386 Packages      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe i386 Packages        
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/multiverse i386 Packages      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/main Translation-en           
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release.gpg                       
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe Translation-en       
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/main Sources                 
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Trovato http://download.ebz.epson.net lsb3.2 Release                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/universe Sources             
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://archive.ubuntu.com trusty-security/restricted Sources           
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Trovato http://archive.ubuntu.com trusty-security/multiverse Sources           
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Trovato http://archive.ubuntu.com trusty-security/main i386 Packages           
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/universe i386 Packages       
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/restricted i386 Packages     
Trovato http://download.ebz.epson.net lsb3.2/main i386 Packages                
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/multiverse i386 Packages     
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-security/universe Translation-en      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it_IT            
Trovato http://archive.ubuntu.com trusty-proposed/main i386 Packages           
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-proposed/universe i386 Packages       
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-proposed/restricted i386 Packages     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-proposed/main Translation-en          
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-proposed/multiverse Translation-en    
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/universe Translation-en      
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/multiverse i386 Packages    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/main i386 Packages          
Trovato http://archive.ubuntu.com trusty-backports/restricted i386 Packages    
Trovato http://archive.ubuntu.com trusty-backports/universe i386 Packages      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/main Translation-en         
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://ppa.launchpad.net jaunty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/universe Translation-en     
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty/main Sources 
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://archive.ubuntu.com trusty/universe Sources                
Trovato http://ppa.launchpad.net trusty/main i386 Packages               
Trovato http://download.ebz.epson.net lsb3.2/main Translation-en         
Trovato http://archive.ubuntu.com trusty/multiverse Sources              
Trovato http://ppa.launchpad.net trusty/main Translation-en              
Trovato http://archive.ubuntu.com trusty/main i386 Packages              
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages              
Trovato http://archive.ubuntu.com trusty/universe i386 Packages         
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://archive.ubuntu.com trusty/main Translation-it
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/restricted Translation-it
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com trusty/restricted Translation-en
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://archive.ubuntu.com trusty/universe Translation-it
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com trusty/universe Translation-en
Trovato http://ppa.launchpad.net trusty/main Translation-en             
Trovato http://ppa.launchpad.net trusty/main Sources                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty Release.gpg
Trovato http://ppa.launchpad.net trusty Release.gpg                        
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources                     
Ign http://archive.ubuntu.com trusty/main Translation-it_IT              
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT        
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT        
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty/main Sources
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en
Trovato http://ppa.launchpad.net trusty Release.gpg
Trovato http://ppa.launchpad.net trusty Release
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net jaunty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net jaunty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net jaunty/main Translation-it_IT                     
Ign http://ppa.launchpad.net jaunty/main Translation-it                        
Ign http://ppa.launchpad.net jaunty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Recuperati 72 B in 14s (4 B/s)                                                 
Lettura elenco dei pacchetti... Fatto


```

About the upgrade, there are errors
```
claudio@claudio:~$ sudo apt-get upgrade
[sudo] password for claudio: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.


```

About the re-installation of Libreoffice I used the commands **sudo add-apt-repository ppa:libreoffice/libreoffice-5-1** 
 and[B] sudo apt-get update && sudo apt-get dist-upgrade
[/B]but I've the same errors of the upgrade

```
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html

This ppa will:
- not contain alpha and beta releases like 5.1.0~beta2
- not contain updates to the next major (5.2.x)
- contain minor release updates and their release candidates -- these can be
  considered stable

Note that for minor release updates (5.1.1, 5.1.2, 5.1.3 ...) an rc2 is almost always exactly the same as the final version.

See: https://wiki.documentfoundation.org/ReleasePlan for details,
and: http://www.libreoffice.org/discover/new-features/ and  https://wiki.documentfoundation.org/ReleaseNotes/5.1 for new features  and fixes.

 Maggiori informazioni: https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-1
Premere [INVIO] per continuare o Ctrl+C per annullare

gpg: portachiavi "/tmp/tmpzkx99o6r/secring.gpg" creato
gpg: portachiavi "/tmp/tmpzkx99o6r/pubring.gpg" creato
gpg: richiesta della chiave 1378B444 dal server hkp keyserver.ubuntu.com
gpg: /tmp/tmpzkx99o6r/trustdb.gpg: creato il trustdb
gpg: chiave 1378B444: chiave pubblica "Launchpad PPA for LibreOffice Packaging" importata
gpg: non è stata trovata alcuna chiave completamente affidabile
gpg: Numero totale esaminato: 1
gpg:               importate: 1  (RSA: 1)
OK
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html

This ppa will:
- not contain alpha and beta releases like 5.1.0~beta2
- not contain updates to the next major (5.2.x)
- contain minor release updates and their release candidates -- these can be
  considered stable

Note that for minor release updates (5.1.1, 5.1.2, 5.1.3 ...) an rc2 is almost always exactly the same as the final version.

See: https://wiki.documentfoundation.org/ReleasePlan for details,
and: http://www.libreoffice.org/discover/new-features/ and  https://wiki.documentfoundation.org/ReleaseNotes/5.1 for new features  and fixes.

 Maggiori informazioni: https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-5-1
Premere [INVIO] per continuare o Ctrl+C per annullare

gpg: portachiavi "/tmp/tmpm_665uct/secring.gpg" creato
gpg: portachiavi "/tmp/tmpm_665uct/pubring.gpg" creato
gpg: richiesta della chiave 1378B444 dal server hkp keyserver.ubuntu.com
gpg: /tmp/tmpm_665uct/trustdb.gpg: creato il trustdb
gpg: chiave 1378B444: chiave pubblica "Launchpad PPA for LibreOffice Packaging" importata
gpg: non è stata trovata alcuna chiave completamente affidabile
gpg: Numero totale esaminato: 1
gpg:               importate: 1  (RSA: 1)
OK
claudio@claudio:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign http://archive.canonical.com trusty InRelease
Ign http://extras.ubuntu.com trusty InRelease                                  
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://extras.ubuntu.com trusty Release.gpg                            
Trovato http://archive.canonical.com trusty Release                            
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://archive.canonical.com trusty/partner Sources                    
Trovato http://extras.ubuntu.com trusty/main Sources                           
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Trovato http://archive.canonical.com trusty/partner Translation-en             
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://deb.playonlinux.com trusty InRelease                            
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://archive.ubuntu.com trusty InRelease                                 
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:1 http://archive.ubuntu.com trusty-updates InRelease [65,9 kB] 
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security InRelease                    
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:2 http://archive.ubuntu.com trusty-proposed InRelease [65,9 kB]
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-backports InRelease                   
Ign http://ppa.launchpad.net jaunty InRelease                                  
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Scaricamento di:3 http://ppa.launchpad.net trusty InRelease [15,5 kB]          
Ign http://download.ebz.epson.net lsb3.2 InRelease                             
Scaricamento di:4 http://archive.ubuntu.com trusty-updates/main Sources [277 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:5 http://archive.ubuntu.com trusty-updates/restricted Sources [5.352 B]
Ign http://ppa.launchpad.net trusty InRelease                                  
Scaricamento di:6 http://archive.ubuntu.com trusty-updates/universe Sources [157 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release.gpg                       
Scaricamento di:7 http://archive.ubuntu.com trusty-updates/multiverse Sources [5.936 B]
Trovato http://ppa.launchpad.net trusty InRelease                              
Scaricamento di:8 http://archive.ubuntu.com trusty-updates/main i386 Packages [748 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://download.ebz.epson.net lsb3.2 Release                           
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Scaricamento di:9 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Scaricamento di:10 http://archive.ubuntu.com trusty-updates/universe i386 Packages [363 kB]
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://download.ebz.epson.net lsb3.2/main i386 Packages                
Scaricamento di:11 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13,6 kB]
Trovato http://archive.ubuntu.com trusty-updates/main Translation-en           
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates/universe Translation-en       
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it_IT            
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-security/main Sources                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://archive.ubuntu.com trusty-security/universe Sources             
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/restricted Sources           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-security/multiverse Sources           
Trovato http://download.ebz.epson.net lsb3.2/main Translation-it               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-security/main i386 Packages           
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/universe i386 Packages       
Trovato http://ppa.launchpad.net trusty/main i386 Packages                
Trovato http://archive.ubuntu.com trusty-security/restricted i386 Packages
Trovato http://ppa.launchpad.net trusty/main Translation-en               
Trovato http://archive.ubuntu.com trusty-security/multiverse i386 Packages     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://download.ebz.epson.net lsb3.2/main Translation-en               
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-security/universe Translation-en      
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Scaricamento di:12 http://archive.ubuntu.com trusty-proposed/main i386 Packages [125 kB]
Trovato http://ppa.launchpad.net trusty/main Sources                           
Scaricamento di:13 http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Scaricamento di:14 http://archive.ubuntu.com trusty-proposed/universe i386 Packages [18,7 kB]
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Scaricamento di:15 http://archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-proposed/main Translation-en          
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-proposed/multiverse Translation-en    
Trovato http://ppa.launchpad.net jaunty Release.gpg                            
Scaricamento di:16 http://ppa.launchpad.net trusty/main i386 Packages [29,7 kB]
Trovato http://archive.ubuntu.com trusty-proposed/restricted Translation-en    
Trovato http://archive.ubuntu.com trusty-proposed/universe Translation-en      
Scaricamento di:17 http://ppa.launchpad.net trusty/main Translation-en [11,6 kB]
Trovato http://archive.ubuntu.com trusty-backports/multiverse i386 Packages    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/main i386 Packages          
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/restricted i386 Packages    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty-backports/universe i386 Packages      
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/main Translation-en         
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty-backports/universe Translation-en     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/main Sources                          
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/universe Sources                      
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/multiverse Sources                    
Trovato http://archive.ubuntu.com trusty/main i386 Packages                    
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages              
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/universe i386 Packages                
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages              
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/main Translation-it                   
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/main Translation-en                   
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it             
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en             
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty/restricted Translation-it             
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty/restricted Translation-en             
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://archive.ubuntu.com trusty/universe Translation-it               
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://archive.ubuntu.com trusty/universe Translation-en               
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Ign http://archive.ubuntu.com trusty/main Translation-it_IT                    
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT              
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT              
Trovato http://ppa.launchpad.net trusty Release                                
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT                
Trovato http://ppa.launchpad.net jaunty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net jaunty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Sources                           
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net jaunty/main Translation-it_IT                     
Ign http://ppa.launchpad.net jaunty/main Translation-it                        
Ign http://ppa.launchpad.net jaunty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Recuperati 1.918 kB in 20s (94,3 kB/s)                                         
Lettura elenco dei pacchetti... Fatto
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.
```

---

### Post by vasa1 on 2016-06-26
What is the output of ```
apt-get purge -s libreoffice*
```

Please note: 
there is no need for adding **sudo** because -s means only a simulation will be done.
Include the command you run, its output and the terminal prompt after that.

Also, there is a mention of Wily here```
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html
```

Maybe you need to use a ppa for Trusty and not Wily: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)

---

### Post by zlatan81 on 2016-06-26
> **vasa1 said:**
> What is the output of ```
apt-get purge -s libreoffice*
```

Please note: 
there is no need for adding **sudo** because -s means only a simulation will be done.
Include the command you run, its output and the terminal prompt after that.

Also, there is a mention of Wily here```
claudio@claudio:~$ sudo add-apt-repository ppa:libreoffice/libreoffice-5-1 
 LibreOffice 5.1.x series stable backports ppa (and SRU-testing for wily)
http://sweetshark.livejournal.com/10977.html
```

Maybe you need to use a ppa for Trusty and not Wily: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)


The output of ```
apt-get purge -s libreoffice
``` is the following:

```
claudio@claudio:~$ apt-get purge -s libreoffice
Nota: questa è solo una simulazione.
      apt-get necessita dei privilegi di root per la normale esecuzione.
      Inoltre, il meccanismo di blocco non è attivato e non è quindi
      utile dare importanza a tutto ciò per una situazione reale.
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Package 'libreoffice' is not installed, so not removed
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non sta per essere installato
 libreoffice-java-common : Dipende: libreoffice-common ma non sta per essere installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non sta per essere installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non sta per essere installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non sta per essere installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).


```

---

### Post by vasa1 on 2016-06-26
See the command I provided! There is an asterisk at the end!

I asked you to run
apt-get purge -s libreoffice*****
You ran
apt-get purge -s libreoffice

Please run the command again correctly. Don't leave out the *****

---

### Post by bapoumba on 2016-06-26
(just to note there still is mention of a jaunty ppa).

---

### Post by vasa1 on 2016-06-26
> **bapoumba said:**
> (just to note there still is mention of a jaunty ppa).
OP was advised to disable unwanted ppas in [post #5]("http://ubuntuforums.org/showthread.php?t=2328871&p=13509221#post13509221") but ...

---

### Post by bapoumba on 2016-06-26
> **vasa1 said:**
> OP was advised to disable unwanted ppas in [post #5]("http://ubuntuforums.org/showthread.php?t=2328871&p=13509221#post13509221") but ...
Yes :)

---

### Post by zlatan81 on 2016-06-26
> **vasa1 said:**
> See the command I provided! There is an asterisk at the end!

I asked you to run
apt-get purge -s libreoffice*****
You ran
apt-get purge -s libreoffice

Please run the command again correctly. Don't leave out the *****


This is the new output:
```
Nota, viene selezionato "libreoffice-mysql-connector" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-xh" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-fa" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-fi" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-fr" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-script-provider-python" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-style-galaxy" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ga" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-gd" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-gl" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-emailmerge" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-nso" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-gu" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-za" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-style-oxygen" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-he" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-hi" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-zu" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-hr" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-hu" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-kde" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-id" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-is" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-it" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-gnome" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-en-gb" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ja" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-avmedia-backend-gstreamer" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-nso" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-grammarcheck-ast" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-style-human" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ka" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-kk" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-km" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ko" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-writer" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-lt" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-lv" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-4.0" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-pt-br" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-4.1" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-4.2" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-4.3" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-l10n-4.4" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-mk" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ml" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-mn" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-mr" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-nb" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ne" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-gtk" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-nl" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-nn" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-nr" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-hyphenation-fi" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-oc" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-style-default" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-om" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-or" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-sdbc-hsqldb" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-4.1" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-4.2" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-pl" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-pt" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-presenter-console" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-style-hicontrast" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-spellcheck-fi" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ro" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-ru" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-help-rw" per l'espressione regolare "libreoffice*"
Nota, viene selezionato "libreoffice-avmedia-backend-gstreamer" al posto di "libreoffice-avmedia-backend"
Package 'libreoffice-gcj' is not installed, so not removed
Package 'libreoffice-filter-mobiledev' is not installed, so not removed
Package 'libreoffice-l10n-3.5' is not installed, so not removed
Package 'libreoffice-l10n-3.6' is not installed, so not removed
Package 'libreoffice-style-andromeda' is not installed, so not removed
Package 'zotero-libreoffice-integration' is not installed, so not removed
Nota, viene selezionato "libreoffice-common" al posto di "libreoffice-l10n-en-us"
Package 'libreoffice-filter-binfilter' is not installed, so not removed
Package 'libreoffice-unbundled' is not installed, so not removed
Package 'libreoffice-evolution' is not installed, so not removed
Package 'libreoffice-kab' is not installed, so not removed
Nota, viene selezionato "browser-plugin-libreoffice" al posto di "mozilla-libreoffice"
Nota, viene selezionato "libreoffice-core" al posto di "libreoffice-bundled"
Nota, viene selezionato "openoffice.org-dtd-officedocument1.0" al posto di "libreoffice-dtd-officedocument1.0"
Nota, viene selezionato "libreoffice-gnome" al posto di "libreoffice-gtk-gnome"
Package 'libreoffice-grammarcheck-af' is not installed, so not removed
Package 'libreoffice-help-af' is not installed, so not removed
Package 'libreoffice-grammarcheck-ar' is not installed, so not removed
Package 'libreoffice-help-ar' is not installed, so not removed
Package 'libreoffice-grammarcheck-as' is not installed, so not removed
Package 'libreoffice-help-as' is not installed, so not removed
Package 'libreoffice-grammarcheck-ast' is not installed, so not removed
Package 'libreoffice-help-ast' is not installed, so not removed
Package 'libreoffice-grammarcheck-be' is not installed, so not removed
Package 'libreoffice-help-be' is not installed, so not removed
Package 'libreoffice-grammarcheck-bg' is not installed, so not removed
Package 'libreoffice-help-bg' is not installed, so not removed
Package 'libreoffice-grammarcheck-bn' is not installed, so not removed
Package 'libreoffice-help-bn' is not installed, so not removed
Package 'libreoffice-grammarcheck-br' is not installed, so not removed
Package 'libreoffice-help-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-bs' is not installed, so not removed
Package 'libreoffice-help-bs' is not installed, so not removed
Package 'libreoffice-grammarcheck-ca' is not installed, so not removed
Package 'libreoffice-grammarcheck-cs' is not installed, so not removed
Package 'libreoffice-grammarcheck-cy' is not installed, so not removed
Package 'libreoffice-help-cy' is not installed, so not removed
Package 'libreoffice-grammarcheck-da' is not installed, so not removed
Package 'libreoffice-grammarcheck-de' is not installed, so not removed
Package 'libreoffice-grammarcheck-dz' is not installed, so not removed
Package 'libreoffice-grammarcheck-el' is not installed, so not removed
Nota, viene selezionato "libreoffice-lightproof-en" al posto di "libreoffice-grammarcheck-en-gb"
Nota, viene selezionato "libreoffice-lightproof-en" al posto di "libreoffice-grammarcheck-en-za"
Package 'libreoffice-help-en-za' is not installed, so not removed
Package 'libreoffice-grammarcheck-eo' is not installed, so not removed
Package 'libreoffice-help-eo' is not installed, so not removed
Package 'libreoffice-grammarcheck-es' is not installed, so not removed
Package 'libreoffice-grammarcheck-et' is not installed, so not removed
Package 'libreoffice-grammarcheck-eu' is not installed, so not removed
Package 'libreoffice-grammarcheck-fa' is not installed, so not removed
Package 'libreoffice-help-fa' is not installed, so not removed
Package 'libreoffice-grammarcheck-fi' is not installed, so not removed
Package 'libreoffice-grammarcheck-fr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ga' is not installed, so not removed
Package 'libreoffice-help-ga' is not installed, so not removed
Package 'libreoffice-grammarcheck-gd' is not installed, so not removed
Package 'libreoffice-help-gd' is not installed, so not removed
Package 'libreoffice-grammarcheck-gl' is not installed, so not removed
Package 'libreoffice-grammarcheck-gu' is not installed, so not removed
Package 'libreoffice-help-gu' is not installed, so not removed
Package 'libreoffice-grammarcheck-he' is not installed, so not removed
Package 'libreoffice-help-he' is not installed, so not removed
Package 'libreoffice-grammarcheck-hi' is not installed, so not removed
Package 'libreoffice-grammarcheck-hr' is not installed, so not removed
Package 'libreoffice-help-hr' is not installed, so not removed
Nota, viene selezionato "libreoffice-lightproof-hu" al posto di "libreoffice-grammarcheck-hu"
Package 'libreoffice-grammarcheck-id' is not installed, so not removed
Package 'libreoffice-help-id' is not installed, so not removed
Package 'libreoffice-grammarcheck-is' is not installed, so not removed
Package 'libreoffice-help-is' is not installed, so not removed
Package 'libreoffice-grammarcheck-it' is not installed, so not removed
Package 'libreoffice-grammarcheck-ja' is not installed, so not removed
Package 'libreoffice-grammarcheck-ka' is not installed, so not removed
Package 'libreoffice-help-ka' is not installed, so not removed
Package 'libreoffice-grammarcheck-kk' is not installed, so not removed
Package 'libreoffice-help-kk' is not installed, so not removed
Package 'libreoffice-grammarcheck-km' is not installed, so not removed
Package 'libreoffice-grammarcheck-kmr-latn' is not installed, so not removed
Package 'libreoffice-help-kmr-latn' is not installed, so not removed
Package 'libreoffice-grammarcheck-ko' is not installed, so not removed
Package 'libreoffice-grammarcheck-lt' is not installed, so not removed
Package 'libreoffice-help-lt' is not installed, so not removed
Package 'libreoffice-grammarcheck-lv' is not installed, so not removed
Package 'libreoffice-help-lv' is not installed, so not removed
Package 'libreoffice-grammarcheck-mk' is not installed, so not removed
Package 'libreoffice-help-mk' is not installed, so not removed
Package 'libreoffice-grammarcheck-ml' is not installed, so not removed
Package 'libreoffice-help-ml' is not installed, so not removed
Package 'libreoffice-grammarcheck-mn' is not installed, so not removed
Package 'libreoffice-help-mn' is not installed, so not removed
Package 'libreoffice-grammarcheck-mr' is not installed, so not removed
Package 'libreoffice-help-mr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nb' is not installed, so not removed
Package 'libreoffice-help-nb' is not installed, so not removed
Package 'libreoffice-grammarcheck-ne' is not installed, so not removed
Package 'libreoffice-help-ne' is not installed, so not removed
Package 'libreoffice-grammarcheck-nl' is not installed, so not removed
Package 'libreoffice-grammarcheck-nn' is not installed, so not removed
Package 'libreoffice-help-nn' is not installed, so not removed
Package 'libreoffice-grammarcheck-nr' is not installed, so not removed
Package 'libreoffice-help-nr' is not installed, so not removed
Package 'libreoffice-grammarcheck-nso' is not installed, so not removed
Package 'libreoffice-help-nso' is not installed, so not removed
Package 'libreoffice-grammarcheck-oc' is not installed, so not removed
Package 'libreoffice-help-oc' is not installed, so not removed
Package 'libreoffice-grammarcheck-om' is not installed, so not removed
Package 'libreoffice-grammarcheck-or' is not installed, so not removed
Package 'libreoffice-help-or' is not installed, so not removed
Package 'libreoffice-grammarcheck-pa-in' is not installed, so not removed
Package 'libreoffice-help-pa-in' is not installed, so not removed
Package 'libreoffice-grammarcheck-pl' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt' is not installed, so not removed
Package 'libreoffice-grammarcheck-pt-br' is not installed, so not removed
Package 'libreoffice-grammarcheck-ro' is not installed, so not removed
Package 'libreoffice-help-ro' is not installed, so not removed
Nota, viene selezionato "libreoffice-lightproof-ru-ru" al posto di "libreoffice-grammarcheck-ru"
Package 'libreoffice-grammarcheck-rw' is not installed, so not removed
Package 'libreoffice-help-rw' is not installed, so not removed
Package 'libreoffice-grammarcheck-si' is not installed, so not removed
Package 'libreoffice-help-si' is not installed, so not removed
Package 'libreoffice-grammarcheck-sk' is not installed, so not removed
Package 'libreoffice-grammarcheck-sl' is not installed, so not removed
Package 'libreoffice-grammarcheck-sr' is not installed, so not removed
Package 'libreoffice-help-sr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ss' is not installed, so not removed
Package 'libreoffice-help-ss' is not installed, so not removed
Package 'libreoffice-grammarcheck-st' is not installed, so not removed
Package 'libreoffice-help-st' is not installed, so not removed
Package 'libreoffice-grammarcheck-sv' is not installed, so not removed
Package 'libreoffice-grammarcheck-ta' is not installed, so not removed
Package 'libreoffice-help-ta' is not installed, so not removed
Package 'libreoffice-grammarcheck-te' is not installed, so not removed
Package 'libreoffice-help-te' is not installed, so not removed
Package 'libreoffice-grammarcheck-tg' is not installed, so not removed
Package 'libreoffice-help-tg' is not installed, so not removed
Package 'libreoffice-grammarcheck-th' is not installed, so not removed
Package 'libreoffice-help-th' is not installed, so not removed
Package 'libreoffice-grammarcheck-tn' is not installed, so not removed
Package 'libreoffice-help-tn' is not installed, so not removed
Package 'libreoffice-grammarcheck-tr' is not installed, so not removed
Package 'libreoffice-grammarcheck-ts' is not installed, so not removed
Package 'libreoffice-help-ts' is not installed, so not removed
Package 'libreoffice-grammarcheck-ug' is not installed, so not removed
Package 'libreoffice-help-ug' is not installed, so not removed
Package 'libreoffice-grammarcheck-uk' is not installed, so not removed
Package 'libreoffice-help-uk' is not installed, so not removed
Package 'libreoffice-grammarcheck-uz' is not installed, so not removed
Package 'libreoffice-help-uz' is not installed, so not removed
Package 'libreoffice-grammarcheck-ve' is not installed, so not removed
Package 'libreoffice-help-ve' is not installed, so not removed
Package 'libreoffice-grammarcheck-vi' is not installed, so not removed
Package 'libreoffice-grammarcheck-xh' is not installed, so not removed
Package 'libreoffice-help-xh' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-cn' is not installed, so not removed
Package 'libreoffice-grammarcheck-zh-tw' is not installed, so not removed
Package 'libreoffice-grammarcheck-zu' is not installed, so not removed
Package 'libreoffice-help-zu' is not installed, so not removed
Nota, viene selezionato "libreoffice-voikko" al posto di "libreoffice-hyphenation-fi"
Nota, viene selezionato "libreoffice-voikko" al posto di "libreoffice-spellcheck-fi"
Nota, viene selezionato "unity-scope-home" al posto di "unity-scope-asklibreoffice"
Package 'libreoffice.org-calc' is not installed, so not removed
Package 'libreoffice.org-writer' is not installed, so not removed
Nota, viene selezionato "libreoffice-lightproof-en" al posto di "libreoffice-grammarcheck-en-us"
Nota, viene selezionato "libreoffice-report-builder" al posto di "libreoffice-reportdesigner"
Nota, viene selezionato "libreoffice-zemberek" al posto di "libreoffice-hyphenation-tr"
Nota, viene selezionato "libreoffice-zemberek" al posto di "libreoffice-spellcheck-tr"
Package 'libreoffice-help-4.2' is not installed, so not removed
Package 'libreoffice-l10n-4.2' is not installed, so not removed
Package 'libreoffice-l10n-4.0' is not installed, so not removed
Package 'libreoffice-l10n-4.3' is not installed, so not removed
Package 'libreoffice-l10n-4.4' is not installed, so not removed
Package 'libreoffice-l10n-5.0' is not installed, so not removed
Package 'libreoffice-grammarcheck-am' is not installed, so not removed
Package 'libreoffice-help-am' is not installed, so not removed
Package 'libreoffice-grammarcheck-gug' is not installed, so not removed
Package 'libreoffice-help-gug' is not installed, so not removed
Package 'libreoffice-nlpsolver' is not installed, so not removed
Package 'libreoffice-voikko' is not installed, so not removed
Package 'libreoffice-accessodf' is not installed, so not removed
Package 'libreoffice-dmaths' is not installed, so not removed
Package 'libreoffice-lightproof-en' is not installed, so not removed
Package 'libreoffice-lightproof-hu' is not installed, so not removed
Package 'libreoffice-lightproof-ru-ru' is not installed, so not removed
Package 'libreoffice-templates' is not installed, so not removed
Package 'libreoffice-writer2latex' is not installed, so not removed
Package 'libreoffice-writer2xhtml' is not installed, so not removed
Package 'libreoffice-zemberek' is not installed, so not removed
Package 'openclipart-libreoffice' is not installed, so not removed
Package 'openclipart2-libreoffice' is not installed, so not removed
Package 'libreoffice-style-crystal' is not installed, so not removed
Package 'libreoffice' is not installed, so not removed
Package 'libreoffice-gtk' is not installed, so not removed
Package 'libreoffice-gnome' is not installed, so not removed
Package 'libreoffice-officebean' is not installed, so not removed
Package 'libreoffice-ogltrans' is not installed, so not removed
Package 'libreoffice-report-builder-bin' is not installed, so not removed
Package 'libreoffice-dbg' is not installed, so not removed
Package 'libreoffice-dev' is not installed, so not removed
Package 'libreoffice-presentation-minimizer' is not installed, so not removed
Package 'libreoffice-presenter-console' is not installed, so not removed
Package 'libreoffice-sdbc-postgresql' is not installed, so not removed
Package 'libreoffice-mysql-connector' is not installed, so not removed
Package 'libreoffice-kde' is not installed, so not removed
Package 'libreoffice-l10n-af' is not installed, so not removed
Package 'libreoffice-l10n-ar' is not installed, so not removed
Package 'libreoffice-l10n-as' is not installed, so not removed
Package 'libreoffice-l10n-ast' is not installed, so not removed
Package 'libreoffice-l10n-bg' is not installed, so not removed
Package 'libreoffice-l10n-bn' is not installed, so not removed
Package 'libreoffice-l10n-br' is not installed, so not removed
Package 'libreoffice-l10n-bs' is not installed, so not removed
Package 'libreoffice-l10n-ca' is not installed, so not removed
Package 'libreoffice-l10n-cs' is not installed, so not removed
Package 'libreoffice-l10n-cy' is not installed, so not removed
Package 'libreoffice-l10n-da' is not installed, so not removed
Package 'libreoffice-l10n-de' is not installed, so not removed
Package 'libreoffice-l10n-dz' is not installed, so not removed
Package 'libreoffice-l10n-el' is not installed, so not removed
Package 'libreoffice-l10n-en-za' is not installed, so not removed
Package 'libreoffice-l10n-eo' is not installed, so not removed
Package 'libreoffice-l10n-es' is not installed, so not removed
Package 'libreoffice-l10n-et' is not installed, so not removed
Package 'libreoffice-l10n-eu' is not installed, so not removed
Package 'libreoffice-l10n-fa' is not installed, so not removed
Package 'libreoffice-l10n-fi' is not installed, so not removed
Package 'libreoffice-l10n-fr' is not installed, so not removed
Package 'libreoffice-l10n-ga' is not installed, so not removed
Package 'libreoffice-l10n-gl' is not installed, so not removed
Package 'libreoffice-l10n-gu' is not installed, so not removed
Package 'libreoffice-l10n-he' is not installed, so not removed
Package 'libreoffice-l10n-hi' is not installed, so not removed
Package 'libreoffice-l10n-hr' is not installed, so not removed
Package 'libreoffice-l10n-hu' is not installed, so not removed
Package 'libreoffice-l10n-id' is not installed, so not removed
Package 'libreoffice-l10n-ja' is not installed, so not removed
Package 'libreoffice-l10n-ka' is not installed, so not removed
Package 'libreoffice-l10n-km' is not installed, so not removed
Package 'libreoffice-l10n-ko' is not installed, so not removed
Package 'libreoffice-l10n-ku' is not installed, so not removed
Package 'libreoffice-l10n-lt' is not installed, so not removed
Package 'libreoffice-l10n-lv' is not installed, so not removed
Package 'libreoffice-l10n-mk' is not installed, so not removed
Package 'libreoffice-l10n-mn' is not installed, so not removed
Package 'libreoffice-l10n-ml' is not installed, so not removed
Package 'libreoffice-l10n-mr' is not installed, so not removed
Package 'libreoffice-l10n-nb' is not installed, so not removed
Package 'libreoffice-l10n-ne' is not installed, so not removed
Package 'libreoffice-l10n-nl' is not installed, so not removed
Package 'libreoffice-l10n-nn' is not installed, so not removed
Package 'libreoffice-l10n-nr' is not installed, so not removed
Package 'libreoffice-l10n-oc' is not installed, so not removed
Package 'libreoffice-l10n-om' is not installed, so not removed
Package 'libreoffice-l10n-or' is not installed, so not removed
Package 'libreoffice-l10n-pa-in' is not installed, so not removed
Package 'libreoffice-l10n-pl' is not installed, so not removed
Package 'libreoffice-l10n-pt' is not installed, so not removed
Package 'libreoffice-l10n-pt-br' is not installed, so not removed
Package 'libreoffice-l10n-ro' is not installed, so not removed
Package 'libreoffice-l10n-ru' is not installed, so not removed
Package 'libreoffice-l10n-rw' is not installed, so not removed
Package 'libreoffice-l10n-si' is not installed, so not removed
Package 'libreoffice-l10n-sk' is not installed, so not removed
Package 'libreoffice-l10n-sl' is not installed, so not removed
Package 'libreoffice-l10n-sr' is not installed, so not removed
Package 'libreoffice-l10n-ss' is not installed, so not removed
Package 'libreoffice-l10n-st' is not installed, so not removed
Package 'libreoffice-l10n-sv' is not installed, so not removed
Package 'libreoffice-l10n-ta' is not installed, so not removed
Package 'libreoffice-l10n-te' is not installed, so not removed
Package 'libreoffice-l10n-tg' is not installed, so not removed
Package 'libreoffice-l10n-th' is not installed, so not removed
Package 'libreoffice-l10n-tn' is not installed, so not removed
Package 'libreoffice-l10n-tr' is not installed, so not removed
Package 'libreoffice-l10n-ts' is not installed, so not removed
Package 'libreoffice-l10n-ug' is not installed, so not removed
Package 'libreoffice-l10n-uk' is not installed, so not removed
Package 'libreoffice-l10n-uz' is not installed, so not removed
Package 'libreoffice-l10n-ve' is not installed, so not removed
Package 'libreoffice-l10n-vi' is not installed, so not removed
Package 'libreoffice-l10n-xh' is not installed, so not removed
Package 'libreoffice-l10n-zh-cn' is not installed, so not removed
Package 'libreoffice-l10n-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-zu' is not installed, so not removed
Package 'libreoffice-help-en-us' is not installed, so not removed
Package 'libreoffice-help-ca' is not installed, so not removed
Package 'libreoffice-help-cs' is not installed, so not removed
Package 'libreoffice-help-da' is not installed, so not removed
Package 'libreoffice-help-de' is not installed, so not removed
Package 'libreoffice-help-dz' is not installed, so not removed
Package 'libreoffice-help-el' is not installed, so not removed
Package 'libreoffice-help-es' is not installed, so not removed
Package 'libreoffice-help-et' is not installed, so not removed
Package 'libreoffice-help-eu' is not installed, so not removed
Package 'libreoffice-help-fi' is not installed, so not removed
Package 'libreoffice-help-fr' is not installed, so not removed
Package 'libreoffice-help-gl' is not installed, so not removed
Package 'libreoffice-help-hi' is not installed, so not removed
Package 'libreoffice-help-hu' is not installed, so not removed
Package 'libreoffice-help-ja' is not installed, so not removed
Package 'libreoffice-help-km' is not installed, so not removed
Package 'libreoffice-help-ko' is not installed, so not removed
Package 'libreoffice-help-nl' is not installed, so not removed
Package 'libreoffice-help-om' is not installed, so not removed
Package 'libreoffice-help-pl' is not installed, so not removed
Package 'libreoffice-help-pt' is not installed, so not removed
Package 'libreoffice-help-pt-br' is not installed, so not removed
Package 'libreoffice-help-ru' is not installed, so not removed
Package 'libreoffice-help-sk' is not installed, so not removed
Package 'libreoffice-help-sl' is not installed, so not removed
Package 'libreoffice-help-sv' is not installed, so not removed
Package 'libreoffice-help-zh-cn' is not installed, so not removed
Package 'libreoffice-help-zh-tw' is not installed, so not removed
Package 'libreoffice-l10n-za' is not installed, so not removed
Package 'libreoffice-l10n-in' is not installed, so not removed
Package 'libreoffice-style-oxygen' is not installed, so not removed
Package 'libreoffice-style-tango' is not installed, so not removed
Package 'libreoffice-style-hicontrast' is not installed, so not removed
Package 'libreoffice-emailmerge' is not installed, so not removed
Package 'libreoffice-dev-doc' is not installed, so not removed
Package 'libreoffice-wiki-publisher' is not installed, so not removed
Package 'libreoffice-report-builder' is not installed, so not removed
Package 'libreoffice-style-human' is not installed, so not removed
Package 'libreoffice-l10n-is' is not installed, so not removed
Package 'libreoffice-script-provider-bsh' is not installed, so not removed
Package 'libreoffice-l10n-be' is not installed, so not removed
Package 'libreoffice-l10n-nso' is not installed, so not removed
Package 'libreoffice-gtk3' is not installed, so not removed
Package 'libreoffice-script-provider-js' is not installed, so not removed
Package 'libreoffice-script-provider-python' is not installed, so not removed
Package 'libreoffice-subsequentcheckbase' is not installed, so not removed
Package 'libreoffice-librelogo' is not installed, so not removed
Package 'libreoffice-help-tr' is not installed, so not removed
Package 'libreoffice-help-vi' is not installed, so not removed
Package 'libreoffice-l10n-kk' is not installed, so not removed
Package 'libreoffice-style-sifr' is not installed, so not removed
Package 'libreoffice-l10n-kmr-latn' is not installed, so not removed
Package 'libreoffice-l10n-gd' is not installed, so not removed
Package 'libreoffice-style-breeze' is not installed, so not removed
Package 'libreofficekit-dev' is not installed, so not removed
Package 'libreoffice-l10n-am' is not installed, so not removed
Package 'libreoffice-l10n-gug' is not installed, so not removed
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 mythes-en-us : Dipende: libreoffice-core ma non sta per essere installato oppure
                         openoffice.org-core (>= 1.9) ma non è installabile oppure
                         language-support-writing-en ma non è installabile
 mythes-it : Dipende: openoffice.org-core (>= 1.9) ma non è installabile oppure
                      libreoffice-core ma non sta per essere installato
 python3-uno : Dipende: libreoffice-core (= 1:5.1.4-0ubuntu1~trusty1) ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).


```

About the PPA, i think that now is disabled

---

### Post by bapoumba on 2016-06-26
Please post the outputs to the following commands, I'm not sure where we are at the moment :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by zlatan81 on 2016-06-26
> **bapoumba said:**
> Please post the outputs to the following commands, I'm not sure where we are at the moment :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

output of cat -n /etc/apt/sources.list:

```
cat -n /etc/apt/sources.list
[sudo] password for claudio: 
E: Opzione a riga di comando "f" [da -f] sconosciuta.
claudio@claudio:~$ sudo cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://archive.ubuntu.com/ubuntu trusty main restricted
     6    deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    11    deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://archive.ubuntu.com/ubuntu trusty universe
    17    deb-src http://archive.ubuntu.com/ubuntu trusty universe
    18    deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    19    deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## 
    25    ##WILL NOT receive any review or updates from the Ubuntu
    26    ## security team.
    27    deb http://archive.ubuntu.com/ubuntu trusty multiverse
    28    deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
    29    deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    30    deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    31    
    32    ## N.B. software from this repository may not have been tested as
    33    ## extensively as that contained in the main release, although it includes
    34    ## newer versions of some applications which may provide useful features.
    35    ## Also, please note that software in backports WILL NOT receive any review
    36    ## or updates from the Ubuntu security team.
    37    
    38    
    39    deb http://archive.ubuntu.com/ubuntu trusty-security main universe restricted multiverse
    40    deb-src http://archive.ubuntu.com/ubuntu trusty-security main universe restricted multiverse
    41    
    42    
    43    ## Uncomment the following two lines to add software from Canonical's
    44    ## 'partner' repository.
    45    ## This software is not part of Ubuntu, but is offered by Canonical and the
    46    ## respective vendors as a service to Ubuntu users.
    47    deb http://archive.canonical.com/ubuntu trusty partner
    48    deb-src http://archive.canonical.com/ubuntu trusty partner
    49    
    50    ## This software is not part of Ubuntu, but is offered by third-party
    51    ## developers who want to ship their latest software.
    52    deb http://extras.ubuntu.com/ubuntu trusty main
    53    deb-src http://extras.ubuntu.com/ubuntu trusty main
    54    deb http://archive.ubuntu.com/ubuntu trusty-proposed main multiverse universe restricted
    55    deb http://download.ebz.epson.net/dsc/op/stable/debian/ lsb3.2 main
    56    deb http://archive.ubuntu.com/ubuntu trusty-backports multiverse main restricted universe
    57    # deb http://archive.ubuntu.com/ubuntu CODENAME main
    58    # deb-src http://archive.ubuntu.com/ubuntu CODENAME main
    59    
    60    deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
    61    # deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
claudio@claudio:~$ 


```


output of ls -la /etc/apt/sources.list.d:

```
ls -la /etc/apt/sources.list.d
totale 288
drwxr-xr-x 2 root root 4096 giu 25 18:18 .
drwxr-xr-x 6 root root 4096 giu 26 13:47 ..
-rw-r--r-- 1 root root  206 giu 26 13:49 atareao-atareao-trusty.list
-rw-r--r-- 1 root root  206 giu 26 13:49 atareao-atareao-trusty.list.save
-rw-r--r-- 1 root root  197 giu 26 13:49 atareao-updf-trusty.list
-rw-r--r-- 1 root root  197 giu 26 13:49 atareao-updf-trusty.list.save
-rw-r--r-- 1 root root  138 giu 26 13:49 cinelerra-ppa-ppa-trusty.list
-rw-r--r-- 1 root root  138 giu 26 13:49 cinelerra-ppa-ppa-trusty.list.save
-rw-r--r-- 1 root root  282 giu 26 13:49 clipgrab-team-ppa-trusty.list
-rw-r--r-- 1 root root  282 giu 26 13:49 clipgrab-team-ppa-trusty.list.save
-rw-r--r-- 1 root root  124 giu 26 13:49 dhor-myway-trusty.list
-rw-r--r-- 1 root root  124 giu 26 13:49 dhor-myway-trusty.list.save
-rw-r--r-- 1 root root  224 giu 26 13:49 ferramroberto-sopcast-trusty.list
-rw-r--r-- 1 root root  224 giu 26 13:49 ferramroberto-sopcast-trusty.list.save
-rw-r--r-- 1 root root  225 giu 26 13:49 ffdiaporamateam-stable-trusty.list
-rw-r--r-- 1 root root  225 giu 26 13:49 ffdiaporamateam-stable-trusty.list.save
-rw-r--r-- 1 root root  150 giu 26 13:49 ffmulticonverter-stable-trusty.list
-rw-r--r-- 1 root root  150 giu 26 13:49 ffmulticonverter-stable-trusty.list.save
-rw-r--r-- 1 root root  156 giu 26 13:49 george-edison55-nitroshare-trusty.list
-rw-r--r-- 1 root root  156 giu 26 13:49 george-edison55-nitroshare-trusty.list.save
-rw-r--r-- 1 root root  128 giu 26 13:49 gma500-emgd-trusty.list
-rw-r--r-- 1 root root  128 giu 26 13:49 gma500-emgd-trusty.list.save
-rw-r--r-- 1 root root  356 giu 26 13:49 gnomebaker-stable-trusty.list
-rw-r--r-- 1 root root  356 giu 26 13:49 gnomebaker-stable-trusty.list.save
-rw-r--r-- 1 root root  178 giu 26 13:49 google-chrome.list
-rw-r--r-- 1 root root  178 giu 26 13:49 google-chrome.list.save
-rw-r--r-- 1 root root  138 giu 26 13:49 gpoweroff-stable-trusty.list
-rw-r--r-- 1 root root  138 giu 26 13:49 gpoweroff-stable-trusty.list.save
-rw-r--r-- 1 root root  142 giu 26 13:49 jd-team-jdownloader-trusty.list
-rw-r--r-- 1 root root  142 giu 26 13:49 jd-team-jdownloader-trusty.list.save
-rw-r--r-- 1 root root   69 giu 26 13:49 launchpad_handbrake.list
-rw-r--r-- 1 root root   69 giu 26 13:49 launchpad_handbrake.list.save
-rw-r--r-- 1 root root  404 giu 26 13:49 libreoffice-libreoffice-5-1-trusty.list
-rw-r--r-- 1 root root  404 giu 26 13:49 libreoffice-libreoffice-5-1-trusty.list.save
-rw-r--r-- 1 root root  204 giu 26 13:49 libreoffice-ppa-trusty.list
-rw-r--r-- 1 root root  204 giu 26 13:49 libreoffice-ppa-trusty.list.save
-rw-r--r-- 1 root root  130 giu 26 13:49 libreplan-ppa-trusty.list
-rw-r--r-- 1 root root  130 giu 26 13:49 libreplan-ppa-trusty.list.save
-rw-r--r-- 1 root root   66 giu 26 13:49 mate-desktop.list
-rw-r--r-- 1 root root   66 giu 26 13:49 mate-desktop.list.save
-rw-r--r-- 1 root root  126 giu 26 13:49 mixxx-mixxx-trusty.list
-rw-r--r-- 1 root root  126 giu 26 13:49 mixxx-mixxx-trusty.list.save
-rw-r--r-- 1 root root    0 apr 17  2014 nemh-gambas3-trusty.list
-rw-r--r-- 1 root root    0 apr 17  2014 nemh-gambas3-trusty.list.save
-rw-r--r-- 1 root root  134 giu 26 13:49 nemh-systemback-trusty.list
-rw-r--r-- 1 root root  134 giu 26 13:49 nemh-systemback-trusty.list.save
-rw-r--r-- 1 root root  198 giu 26 13:49 noobslab-apps-trusty.list
-rw-r--r-- 1 root root  198 giu 26 13:49 noobslab-apps-trusty.list.save
-rw-r--r-- 1 root root  132 giu 26 13:49 novacut-stable-trusty.list
-rw-r--r-- 1 root root  132 giu 26 13:49 novacut-stable-trusty.list.save
-rw-r--r-- 1 root root  122 giu 26 13:49 numix-ppa-trusty.list
-rw-r--r-- 1 root root  122 giu 26 13:49 numix-ppa-trusty.list.save
-rw-r--r-- 1 root root   44 giu 26 13:49 playonlinux.list
-rw-r--r-- 1 root root   44 giu 26 13:49 playonlinux.list.save
-rw-r--r-- 1 root root  132 giu 26 13:49 screenlets-ppa-trusty.list
-rw-r--r-- 1 root root  134 giu 26 13:49 screenlets-ppa-trusty.list.save
-rw-r--r-- 1 root root  158 giu 26 13:49 stebbins-handbrake-releases-trusty.list
-rw-r--r-- 1 root root  158 giu 26 13:49 stebbins-handbrake-releases-trusty.list.save
-rw-r--r-- 1 root root  152 giu 26 13:49 taskcoach-developers-ppa-trusty.list
-rw-r--r-- 1 root root  152 giu 26 13:49 taskcoach-developers-ppa-trusty.list.save
-rw-r--r-- 1 root root  225 giu 26 13:49 thefanclub-grive-tools-trusty.list
-rw-r--r-- 1 root root  225 giu 26 13:49 thefanclub-grive-tools-trusty.list.save
-rw-r--r-- 1 root root  130 giu 26 13:49 tualatrix-ppa-trusty.list
-rw-r--r-- 1 root root  130 giu 26 13:49 tualatrix-ppa-trusty.list.save
-rw-r--r-- 1 root root  134 giu 26 13:49 ubuntu-wine-ppa-trusty.list
-rw-r--r-- 1 root root  134 giu 26 13:49 ubuntu-wine-ppa-trusty.list.save
-rw-r--r-- 1 root root  150 giu 26 13:49 ubuntu-x-swat-x-updates-trusty.list
-rw-r--r-- 1 root root  150 giu 26 13:49 ubuntu-x-swat-x-updates-trusty.list.save
-rw-r--r-- 1 root root  207 giu 26 13:49 webupd8team-java-trusty.list
-rw-r--r-- 1 root root  207 giu 26 13:49 webupd8team-java-trusty.list.save
-rw-r--r-- 1 root root  134 giu 26 13:49 xorg-edgers-ppa-trusty.list
-rw-r--r-- 1 root root  134 giu 26 13:49 xorg-edgers-ppa-trusty.list.save
-rw-r--r-- 1 root root    0 apr 17  2014 yannubuntu-boot-repair-trusty.list
-rw-r--r-- 1 root root    0 apr 17  2014 yannubuntu-boot-repair-trusty.list.save
-rw-r--r-- 1 root root  124 giu 26 13:49 yktooo-ppa-trusty.list
-rw-r--r-- 1 root root  124 giu 26 13:49 yktooo-ppa-trusty.list.save
```

output of tail -v -n +1 /etc/apt/sources.list.d/*:

```
tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/atareao-atareao-trusty.list <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-atareao-trusty.list.save <==
# deb http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/atareao/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-updf-trusty.list <==
# deb http://ppa.launchpad.net/atareao/updf/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/updf/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/updf/ubuntu trusty main

==> /etc/apt/sources.list.d/atareao-updf-trusty.list.save <==
# deb http://ppa.launchpad.net/atareao/updf/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/updf/ubuntu trusty main
# deb-src http://ppa.launchpad.net/atareao/updf/ubuntu trusty main

==> /etc/apt/sources.list.d/cinelerra-ppa-ppa-trusty.list <==
deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/cinelerra-ppa-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/cinelerra-ppa/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/clipgrab-team-ppa-trusty.list <==
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/clipgrab-team-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/dhor-myway-trusty.list <==
deb http://ppa.launchpad.net/dhor/myway/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dhor/myway/ubuntu trusty main

==> /etc/apt/sources.list.d/dhor-myway-trusty.list.save <==
deb http://ppa.launchpad.net/dhor/myway/ubuntu trusty main
# deb-src http://ppa.launchpad.net/dhor/myway/ubuntu trusty main

==> /etc/apt/sources.list.d/ferramroberto-sopcast-trusty.list <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main

==> /etc/apt/sources.list.d/ferramroberto-sopcast-trusty.list.save <==
# deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu trusty main

==> /etc/apt/sources.list.d/ffdiaporamateam-stable-trusty.list <==
deb http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/ffdiaporamateam-stable-trusty.list.save <==
deb http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffdiaporamateam/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list <==
deb http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list.save <==
deb http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/george-edison55-nitroshare-trusty.list <==
deb http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu trusty main
# deb-src http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu trusty main

==> /etc/apt/sources.list.d/george-edison55-nitroshare-trusty.list.save <==
deb http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu trusty main
# deb-src http://ppa.launchpad.net/george-edison55/nitroshare/ubuntu trusty main

==> /etc/apt/sources.list.d/gma500-emgd-trusty.list <==
# deb http://ppa.launchpad.net/gma500/emgd/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gma500/emgd/ubuntu trusty main

==> /etc/apt/sources.list.d/gma500-emgd-trusty.list.save <==
# deb http://ppa.launchpad.net/gma500/emgd/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gma500/emgd/ubuntu trusty main

==> /etc/apt/sources.list.d/gnomebaker-stable-trusty.list <==
# deb http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/gnomebaker-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gnomebaker/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/gpoweroff-stable-trusty.list <==
# deb http://ppa.launchpad.net/gpoweroff/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gpoweroff/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/gpoweroff-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/gpoweroff/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/gpoweroff/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/jd-team-jdownloader-trusty.list <==
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main
# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main

==> /etc/apt/sources.list.d/jd-team-jdownloader-trusty.list.save <==
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main
# deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu trusty main

==> /etc/apt/sources.list.d/launchpad_handbrake.list <==
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu jaunty main

==> /etc/apt/sources.list.d/launchpad_handbrake.list.save <==
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu jaunty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-1-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-1-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreplan-ppa-trusty.list <==
deb http://ppa.launchpad.net/libreplan/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreplan/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/libreplan-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/libreplan/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreplan/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/mate-desktop.list <==
# deb http://repo.mate-desktop.org/archive/1.8/ubuntu trusty main

==> /etc/apt/sources.list.d/mate-desktop.list.save <==
# deb http://repo.mate-desktop.org/archive/1.8/ubuntu trusty main

==> /etc/apt/sources.list.d/mixxx-mixxx-trusty.list <==
deb http://ppa.launchpad.net/mixxx/mixxx/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mixxx/mixxx/ubuntu trusty main

==> /etc/apt/sources.list.d/mixxx-mixxx-trusty.list.save <==
deb http://ppa.launchpad.net/mixxx/mixxx/ubuntu trusty main
# deb-src http://ppa.launchpad.net/mixxx/mixxx/ubuntu trusty main

==> /etc/apt/sources.list.d/nemh-gambas3-trusty.list <==

==> /etc/apt/sources.list.d/nemh-gambas3-trusty.list.save <==

==> /etc/apt/sources.list.d/nemh-systemback-trusty.list <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu trusty main

==> /etc/apt/sources.list.d/nemh-systemback-trusty.list.save <==
deb http://ppa.launchpad.net/nemh/systemback/ubuntu trusty main
# deb-src http://ppa.launchpad.net/nemh/systemback/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-apps-trusty.list <==
deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main

==> /etc/apt/sources.list.d/noobslab-apps-trusty.list.save <==
deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main

==> /etc/apt/sources.list.d/novacut-stable-trusty.list <==
deb http://ppa.launchpad.net/novacut/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/novacut/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/novacut-stable-trusty.list.save <==
deb http://ppa.launchpad.net/novacut/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/novacut/stable/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/numix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/numix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/numix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/playonlinux.list <==
deb http://deb.playonlinux.com/ trusty main

==> /etc/apt/sources.list.d/playonlinux.list.save <==
deb http://deb.playonlinux.com/ trusty main

==> /etc/apt/sources.list.d/screenlets-ppa-trusty.list <==
deb http://ppa.launchpad.net/screenlets/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/screenlets-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/screenlets/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/screenlets/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.save <==
deb http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main
# deb-src http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu trusty main

==> /etc/apt/sources.list.d/taskcoach-developers-ppa-trusty.list <==
deb http://ppa.launchpad.net/taskcoach-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/taskcoach-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/taskcoach-developers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/taskcoach-developers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/taskcoach-developers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/thefanclub-grive-tools-trusty.list <==
deb http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main

==> /etc/apt/sources.list.d/thefanclub-grive-tools-trusty.list.save <==
deb http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main
# deb-src http://ppa.launchpad.net/thefanclub/grive-tools/ubuntu trusty main

==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-trusty.list <==
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu trusty main

==> /etc/apt/sources.list.d/ubuntu-x-swat-x-updates-trusty.list.save <==
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu trusty main
# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/webupd8team-java-trusty.list.save <==
deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main
# deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list <==

==> /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list.save <==

==> /etc/apt/sources.list.d/yktooo-ppa-trusty.list <==
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/yktooo/ppa/ubuntu trusty main

==> /etc/apt/sources.list.d/yktooo-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/yktooo/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/yktooo/ppa/ubuntu trusty main


```

---

### Post by bapoumba on 2016-06-26
> 55    deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main
60    deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
In your sources.list, please disable lines 55 and 60 (add a # in front of the line).


> ==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-1-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-libreoffice-5-1-trusty.list.save <==
deb [http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu](http://ppa.launchpad.net/libreoffice/libreoffice-5-1/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main

==> /etc/apt/sources.list.d/libreoffice-ppa-trusty.list.save <==
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) trusty main
Remove all the libreoffice ppas (the ones for 5.1 and the trusty ones, 4 total)

> ==> /etc/apt/sources.list.d/launchpad_handbrake.list <==
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main

==> /etc/apt/sources.list.d/launchpad_handbrake.list.save <==
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) jaunty main
Remove both handbrake Jaunty ppas (2).

Once done, please run :
```
sudo apt-get update
sudo apt-get upgrade
```

All the commands I gave you in the previous post do not require sudo and can be run with your regular user privileges. You do need it to run apt-get though.

---

### Post by zlatan81 on 2016-06-26
> **bapoumba said:**
> In your sources.list, please disable lines 55 and 60 (add a # in front of the line).



Remove all the libreoffice ppas (the ones for 5.1 and the trusty ones, 4 total)


Remove both handbrake Jaunty ppas (2).

Once done, please run :
```
sudo apt-get update
sudo apt-get upgrade
```

All the commands I gave you in the previous post do not require sudo and can be run with your regular user privileges. You do need it to run apt-get though.


output of update:

```
claudio@claudio:~$ sudo apt-get update
Ign http://extras.ubuntu.com trusty InRelease
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://extras.ubuntu.com trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://extras.ubuntu.com trusty Release                                
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://extras.ubuntu.com trusty/main Sources                           
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://extras.ubuntu.com trusty/main i386 Packages                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty/main Translation-it                        
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Trovato http://ppa.launchpad.net trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://ppa.launchpad.net trusty Release.gpg                            
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty Release                                
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://archive.ubuntu.com trusty InRelease                                 
Trovato http://deb.playonlinux.com trusty InRelease                            
Ign http://archive.canonical.com trusty InRelease                              
Trovato http://archive.ubuntu.com trusty-updates InRelease                     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.canonical.com trusty Release.gpg                        
Trovato http://deb.playonlinux.com trusty/main i386 Packages                   
Trovato http://archive.ubuntu.com trusty-security InRelease                    
Trovato http://archive.canonical.com trusty Release                            
Trovato http://archive.ubuntu.com trusty-proposed InRelease                    
Trovato http://archive.canonical.com trusty/partner Sources                    
Trovato http://archive.ubuntu.com trusty-backports InRelease                   
Trovato http://archive.canonical.com trusty/partner i386 Packages              
Trovato http://archive.ubuntu.com trusty Release.gpg                           
Trovato http://archive.canonical.com trusty/partner Translation-en             
Trovato http://archive.ubuntu.com trusty-updates/main Sources                  
Trovato http://archive.ubuntu.com trusty-updates/restricted Sources            
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-updates/universe Sources              
Trovato http://archive.ubuntu.com trusty-updates/multiverse Sources            
Trovato http://archive.ubuntu.com trusty-updates/main i386 Packages            
Trovato http://archive.ubuntu.com trusty-updates/restricted i386 Packages      
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-updates/universe i386 Packages        
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-updates/multiverse i386 Packages      
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Trovato http://archive.ubuntu.com trusty-updates/main Translation-en           
Trovato http://ppa.launchpad.net trusty/main Translation-en                    
Trovato http://archive.ubuntu.com trusty-updates/multiverse Translation-en     
Trovato http://ppa.launchpad.net trusty/main i386 Packages                
Trovato http://archive.ubuntu.com trusty-updates/restricted Translation-en     
Trovato http://archive.ubuntu.com trusty-updates/universe Translation-en       
Ign http://deb.playonlinux.com trusty/main Translation-it_IT                   
Ign http://deb.playonlinux.com trusty/main Translation-it                      
Trovato http://archive.ubuntu.com trusty-security/main Sources                 
Trovato http://ppa.launchpad.net trusty/main i386 Packages                     
Ign http://deb.playonlinux.com trusty/main Translation-en                      
Trovato http://archive.ubuntu.com trusty-security/universe Sources             
Trovato http://archive.ubuntu.com trusty-security/restricted Sources           
Trovato http://archive.ubuntu.com trusty-security/multiverse Sources           
Trovato http://archive.ubuntu.com trusty-security/main i386 Packages           
Trovato http://archive.ubuntu.com trusty-security/universe i386 Packages       
Trovato http://archive.ubuntu.com trusty-security/restricted i386 Packages     
Trovato http://archive.ubuntu.com trusty-security/multiverse i386 Packages     
Trovato http://archive.ubuntu.com trusty-security/main Translation-en          
Trovato http://archive.ubuntu.com trusty-security/multiverse Translation-en    
Trovato http://archive.ubuntu.com trusty-security/restricted Translation-en    
Trovato http://archive.ubuntu.com trusty-security/universe Translation-en      
Trovato http://archive.ubuntu.com trusty-proposed/main i386 Packages           
Trovato http://archive.ubuntu.com trusty-proposed/multiverse i386 Packages     
Trovato http://archive.ubuntu.com trusty-proposed/universe i386 Packages       
Trovato http://archive.ubuntu.com trusty-proposed/restricted i386 Packages     
Trovato http://archive.ubuntu.com trusty-proposed/main Translation-en          
Trovato http://archive.ubuntu.com trusty-proposed/multiverse Translation-en    
Trovato http://archive.ubuntu.com trusty-proposed/restricted Translation-en    
Trovato http://archive.ubuntu.com trusty-proposed/universe Translation-en      
Trovato http://archive.ubuntu.com trusty-backports/multiverse i386 Packages    
Trovato http://archive.ubuntu.com trusty-backports/main i386 Packages          
Trovato http://archive.ubuntu.com trusty-backports/restricted i386 Packages    
Trovato http://archive.ubuntu.com trusty-backports/universe i386 Packages      
Trovato http://archive.ubuntu.com trusty-backports/main Translation-en         
Trovato http://archive.ubuntu.com trusty-backports/multiverse Translation-en   
Trovato http://archive.ubuntu.com trusty-backports/restricted Translation-en   
Trovato http://archive.ubuntu.com trusty-backports/universe Translation-en     
Trovato http://archive.ubuntu.com trusty Release                               
Trovato http://archive.ubuntu.com trusty/main Sources                          
Trovato http://archive.ubuntu.com trusty/restricted Sources                    
Trovato http://archive.ubuntu.com trusty/universe Sources                      
Trovato http://archive.ubuntu.com trusty/multiverse Sources                    
Trovato http://archive.ubuntu.com trusty/main i386 Packages                    
Trovato http://archive.ubuntu.com trusty/restricted i386 Packages              
Trovato http://archive.ubuntu.com trusty/universe i386 Packages                
Trovato http://archive.ubuntu.com trusty/multiverse i386 Packages              
Trovato http://archive.ubuntu.com trusty/main Translation-it                   
Trovato http://archive.ubuntu.com trusty/main Translation-en                   
Trovato http://archive.ubuntu.com trusty/multiverse Translation-it             
Trovato http://archive.ubuntu.com trusty/multiverse Translation-en             
Trovato http://archive.ubuntu.com trusty/restricted Translation-it             
Trovato http://archive.ubuntu.com trusty/restricted Translation-en             
Trovato http://archive.ubuntu.com trusty/universe Translation-it               
Trovato http://archive.ubuntu.com trusty/universe Translation-en               
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty/main Translation-it_IT                    
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://archive.ubuntu.com trusty/multiverse Translation-it_IT              
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://archive.ubuntu.com trusty/restricted Translation-it_IT              
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty/universe Translation-it_IT                
Ign http://ppa.launchpad.net trusty/main Translation-it_IT                     
Ign http://ppa.launchpad.net trusty/main Translation-it                        
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Lettura elenco dei pacchetti... Fatto  

```

output of upgrade:

```
claudio@claudio:~$ sudo apt-get upgrade
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere ciò.
I seguenti pacchetti hanno dipendenze non soddisfatte:
 libreoffice-core : Dipende: libreoffice-common (> 1:5.1.4) ma non è installato
 libreoffice-java-common : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-en-gb : Dipende: libreoffice-common ma non è installato
 libreoffice-l10n-it : Dipende: libreoffice-common ma non è installato
 libreoffice-style-elementary : Dipende: libreoffice-common ma non è installato
 libreoffice-style-galaxy : Dipende: libreoffice-common ma non è installato
E: Dipendenze non trovate. Riprovare usando -f.


```

---

### Post by bapoumba on 2016-06-26
So please run : 
```
sudo apt-get -f install
```

---

### Post by zlatan81 on 2016-06-26
> **bapoumba said:**
> So please run : 
```
sudo apt-get -f install
```

you are great!!! :D:D:D I think that now it's OK!
Removed obsoletes files and software center now work.
I wait your OK to change the thread in SOLVED.

Thank you so much!!! 

Here the output:

```
claudio@claudio:~$ sudo apt-get -f install
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Correzione delle dipendenze... Fatto
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  libapache-pom-java libcommons-logging-java libcommons-parent-java
  libcuda1-331 libcuda1-340 libgconf2-4 libjline-java liblog4j1.2-java
  mythes-en-au nvidia-opencl-icd-331
Usare "apt-get autoremove" per rimuoverli.
I seguenti pacchetti saranno RIMOSSI:
  browser-plugin-libreoffice libreoffice-avmedia-backend-gstreamer
  libreoffice-base libreoffice-base-core libreoffice-base-drivers
  libreoffice-calc libreoffice-core libreoffice-draw libreoffice-help-en-gb
  libreoffice-help-it libreoffice-impress libreoffice-java-common
  libreoffice-l10n-en-gb libreoffice-l10n-it libreoffice-math
  libreoffice-pdfimport libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  libreoffice-style-elementary libreoffice-style-galaxy libreoffice-writer
  mythes-en-us mythes-it python3-uno
0 aggiornati, 0 installati, 24 da rimuovere e 364 non aggiornati.
24 non completamente installati o rimossi.
Dopo quest'operazione, verranno liberati 290 MB di spazio su disco.
Continuare? [S/n] s
(Lettura del database... 292273 file e directory attualmente installati.)
Rimozione di browser-plugin-libreoffice (1:4.2.8-0ubuntu4)...
Rimozione di libreoffice-avmedia-backend-gstreamer (1:4.2.8-0ubuntu4)...
Rimozione di libreoffice-base (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di "deviazione di /usr/lib/libreoffice/share/basic/dialog.xlc in /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess da libreoffice-base"
Rimozione di "deviazione di /usr/lib/libreoffice/share/basic/script.xlc in /usr/lib/libreoffice/share/basic/script.xlc.noaccess da libreoffice-base"
Rimozione di libreoffice-calc (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-help-it (1:4.2.8-0ubuntu1)...
Rimozione di libreoffice-writer (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-base-core (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-base-drivers (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-impress (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-draw (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-pdfimport (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-core (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-help-en-gb (1:4.2.8-0ubuntu1)...
Rimozione di libreoffice-sdbc-hsqldb (1:4.2.8-0ubuntu4)...
Rimozione di libreoffice-java-common (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-l10n-en-gb (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-l10n-it (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-math (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-sdbc-firebird (1:4.2.8-0ubuntu4)...
Rimozione di libreoffice-style-elementary (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di libreoffice-style-galaxy (1:5.1.4-0ubuntu1~trusty1)...
Rimozione di mythes-en-us (1:4.2.1-0ubuntu1.1)...
Rimozione di mythes-it (2.0.7.gh.deb1-4.1)...
Rimozione di python3-uno (1:5.1.4-0ubuntu1~trusty1)...
Elaborazione dei trigger per mime-support (3.54ubuntu1.1)...
Elaborazione dei trigger per gnome-menus (3.10.1-0ubuntu2)...
Elaborazione dei trigger per desktop-file-utils (0.22-1ubuntu1)...
Elaborazione dei trigger per man-db (2.6.7.1-1ubuntu1)...
Elaborazione dei trigger per postgresql-common (154ubuntu1)...
Building PostgreSQL dictionaries from installed myspell/hunspell packages...
  en_au
  en_ca
  en_gb
  en_us
  en_za
  it_it
Removing obsolete dictionary files:


```

---

### Post by bapoumba on 2016-06-26
Hey, glad to see you got it to work :)
You do not need my OK to mark the thread solved. If it is solved for you, please go ahead.

In the future : use ppas with caution ;)

Edit : thanks vasa for pointing it out, you still have packages that need to be upgraded. So please run :
```
sudo apt-get update
sudo apt-get upgrade
```

---

