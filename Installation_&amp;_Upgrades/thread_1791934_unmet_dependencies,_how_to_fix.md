---
title: "unmet dependencies, how to fix?"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by DayLite on 2011-06-27
```
The following packages have unmet dependencies:
 firefox : Depends: libasound2 (> 1.0.24.1)
E: Broken packages

```

How do I fix:confused: I already tried in the package manager and it said no unbroken packages. I rebooted into repair mode and it couldn't fix it. I also used the terminal to fix broken packages, it said it couldn't resolve.  I tried to install libasound2 (> 1.0.24.1) and couldn't.

---

### Post by dabl on 2011-06-27
In a terminal do

```
sudo apt-get update && sudo apt-cache policy libasound2
```

What does the message say?

---

### Post by DayLite on 2011-06-27
> **dabl said:**
> In a terminal do

```
sudo apt-get update && sudo apt-cache policy libasound2
```

What does the message say?

```
joan@joan-laptop:~$ sudo apt-get update && sudo apt-cache policy libasound2
[sudo] password for joan: 
Sorry, try again.
[sudo] password for joan: 
Ign http://mirror.hmc.edu natty InRelease
Ign http://mirror.hmc.edu natty-security InRelease                             
Ign http://mirror.hmc.edu natty-updates InRelease                              
Hit http://mirror.hmc.edu natty Release.gpg                                    
Hit http://mirror.hmc.edu natty-security Release.gpg                           
Hit http://mirror.hmc.edu natty-updates Release.gpg                            
Hit http://mirror.hmc.edu natty Release                                        
Hit http://mirror.hmc.edu natty-security Release                               
Ign http://us.archive.ubuntu.com lucid-backports InRelease                     
Hit http://mirror.hmc.edu natty-updates Release                                
Hit http://packages.medibuntu.org natty InRelease                              
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://mirror.hmc.edu natty/universe Sources                               
Hit http://mirror.hmc.edu natty/main Sources                                   
Hit http://mirror.hmc.edu natty/multiverse Sources                             
Hit http://mirror.hmc.edu natty/restricted Sources                             
Hit http://mirror.hmc.edu natty/main i386 Packages                             
Hit http://mirror.hmc.edu natty/universe i386 Packages                         
Hit http://mirror.hmc.edu natty/restricted i386 Packages                       
Hit http://mirror.hmc.edu natty/multiverse i386 Packages                       
Ign http://mirror.hmc.edu natty/main TranslationIndex                          
Ign http://mirror.hmc.edu natty/multiverse TranslationIndex                    
Ign http://mirror.hmc.edu natty/restricted TranslationIndex                    
Ign http://mirror.hmc.edu natty/universe TranslationIndex                      
Hit http://mirror.hmc.edu natty-security/main Sources                          
Hit http://mirror.hmc.edu natty-security/universe Sources                      
Hit http://mirror.hmc.edu natty-security/restricted Sources                    
Hit http://mirror.hmc.edu natty-security/multiverse Sources                    
Hit http://mirror.hmc.edu natty-security/main i386 Packages                    
Hit http://mirror.hmc.edu natty-security/universe i386 Packages                
Hit http://mirror.hmc.edu natty-security/restricted i386 Packages              
Hit http://mirror.hmc.edu natty-security/multiverse i386 Packages              
Ign http://mirror.hmc.edu natty-security/main TranslationIndex                 
Ign http://mirror.hmc.edu natty-security/multiverse TranslationIndex           
Ign http://mirror.hmc.edu natty-security/restricted TranslationIndex           
Ign http://mirror.hmc.edu natty-security/universe TranslationIndex             
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://mirror.hmc.edu natty-updates/main Sources                           
Hit http://mirror.hmc.edu natty-updates/universe Sources                       
Hit http://mirror.hmc.edu natty-updates/restricted Sources                     
Hit http://mirror.hmc.edu natty-updates/multiverse Sources                     
Hit http://mirror.hmc.edu natty-updates/main i386 Packages                     
Hit http://mirror.hmc.edu natty-updates/universe i386 Packages                 
Hit http://mirror.hmc.edu natty-updates/restricted i386 Packages               
Hit http://mirror.hmc.edu natty-updates/multiverse i386 Packages               
Ign http://mirror.hmc.edu natty-updates/main TranslationIndex                  
Ign http://mirror.hmc.edu natty-updates/multiverse TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/restricted TranslationIndex            
Ign http://mirror.hmc.edu natty-updates/universe TranslationIndex              
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://packages.medibuntu.org natty/free i386 Packages                     
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://packages.medibuntu.org natty/non-free i386 Packages                 
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://mirror.hmc.edu natty/main Translation-en_US                         
Ign http://mirror.hmc.edu natty/main Translation-en                            
Ign http://mirror.hmc.edu natty/multiverse Translation-en_US                   
Ign http://mirror.hmc.edu natty/multiverse Translation-en                      
Ign http://mirror.hmc.edu natty/restricted Translation-en_US                   
Ign http://mirror.hmc.edu natty/restricted Translation-en                      
Ign http://mirror.hmc.edu natty/universe Translation-en_US                     
Ign http://mirror.hmc.edu natty/universe Translation-en                        
Ign http://mirror.hmc.edu natty-security/main Translation-en_US                
Ign http://mirror.hmc.edu natty-security/main Translation-en                   
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en_US          
Ign http://mirror.hmc.edu natty-security/multiverse Translation-en             
Ign http://mirror.hmc.edu natty-security/restricted Translation-en_US          
Ign http://mirror.hmc.edu natty-security/restricted Translation-en             
Ign http://mirror.hmc.edu natty-security/universe Translation-en_US            
Ign http://mirror.hmc.edu natty-security/universe Translation-en               
Ign http://mirror.hmc.edu natty-updates/main Translation-en_US                 
Ign http://mirror.hmc.edu natty-updates/main Translation-en                    
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/multiverse Translation-en              
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en_US           
Ign http://mirror.hmc.edu natty-updates/restricted Translation-en              
Ign http://mirror.hmc.edu natty-updates/universe Translation-en_US             
Ign http://mirror.hmc.edu natty-updates/universe Translation-en                
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en       
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com natty/partner Sources                         
Hit http://ppa.launchpad.net natty Release                                     
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Hit http://archive.canonical.com natty/partner i386 Packages                   
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://ppa.launchpad.net natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://ppa.launchpad.net natty/main i386 Packages                          
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://archive.canonical.com natty/partner Translation-en                  
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US 
Ign http://ppa.launchpad.net natty/main Translation-en    
Ign http://ppa.launchpad.net natty/main Translation-en_US 
Ign http://ppa.launchpad.net natty/main Translation-en    
Ign http://ppa.launchpad.net natty/main Translation-en_US 
Ign http://ppa.launchpad.net natty/main Translation-en    
Ign http://packages.medibuntu.org natty/free Translation-en_US
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Reading package lists... Done
libasound2:
  Installed: 1.0.23-1ubuntu2.1
  Candidate: 1.0.24.1-0ubuntu5
  Version table:
     1.0.24.1-0ubuntu5 0
        500 http://mirror.hmc.edu/ubuntu/ natty/main i386 Packages
 *** 1.0.23-1ubuntu2.1 0
        100 /var/lib/dpkg/status
joan@joan-laptop:~$ 
 
```

---

