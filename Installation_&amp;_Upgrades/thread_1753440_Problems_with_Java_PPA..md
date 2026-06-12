---
title: "Problems with Java PPA."
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by Crabaroni on 2011-05-09
In synaptic it says the sun-java6-jre package is broken. I re-downloaded the repository but that doesn't help. I can't install anything. When I try it gets to 99% and cannot get the "headers". This is what happens when I sudo apt-get update.
```
Crabaroni@Crabaroni-DX4850:~$ sudo apt-get update
[sudo] password for Crabaroni: 
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://dl.google.com stable InRelease                                      
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://archive.canonical.com maverick InRelease                            
Ign http://security.ubuntu.com natty-security InRelease                        
Hit http://packages.medibuntu.org natty InRelease                              
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Hit http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release.gpg                                 
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://archive.canonical.com natty Release.gpg                             
Hit http://security.ubuntu.com natty-security Release.gpg                      
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Ign http://ppa.launchpad.net natty Release.gpg                                 
Hit http://extras.ubuntu.com natty Release                                     
Hit http://archive.canonical.com maverick Release.gpg                          
Hit http://security.ubuntu.com natty-security Release                          
Get:3 http://dl.google.com stable/main amd64 Packages [1,073 B]                
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://us.archive.ubuntu.com natty-updates Release.gpg                     
Hit http://ppa.launchpad.net natty Release                                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com natty Release                                 
Hit http://extras.ubuntu.com natty/main Sources                                
Hit http://security.ubuntu.com natty-security/main Sources                     
Hit http://us.archive.ubuntu.com natty Release                                 
Ign http://ppa.launchpad.net natty Release                                     
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com natty/main amd64 Packages                         
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Hit http://security.ubuntu.com natty-security/restricted Sources               
Hit http://security.ubuntu.com natty-security/universe Sources                 
Hit http://security.ubuntu.com natty-security/multiverse Sources               
Hit http://security.ubuntu.com natty-security/main amd64 Packages              
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages        
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://us.archive.ubuntu.com natty-updates Release                         
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Hit http://security.ubuntu.com natty-security/universe amd64 Packages          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages        
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main amd64 Packages                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://archive.canonical.com maverick/partner amd64 Packages               
Hit http://packages.medibuntu.org natty/free amd64 Packages                    
Ign http://archive.canonical.com maverick/partner TranslationIndex             
Hit http://us.archive.ubuntu.com natty/restricted amd64 Packages               
Hit http://us.archive.ubuntu.com natty/universe amd64 Packages                 
Hit http://us.archive.ubuntu.com natty/multiverse amd64 Packages               
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Hit http://us.archive.ubuntu.com natty-updates/main Sources                    
Hit http://us.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://us.archive.ubuntu.com natty-updates/universe Sources                
Hit http://us.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://us.archive.ubuntu.com natty-updates/main amd64 Packages             
Hit http://us.archive.ubuntu.com natty-updates/restricted amd64 Packages       
Hit http://us.archive.ubuntu.com natty-updates/universe amd64 Packages         
Hit http://us.archive.ubuntu.com natty-updates/multiverse amd64 Packages       
Hit http://packages.medibuntu.org natty/non-free amd64 Packages                
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Err http://ppa.launchpad.net natty/main Sources                                
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages                         
  404  Not Found
Ign http://extras.ubuntu.com natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.canonical.com natty/partner Translation-en_US               
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.canonical.com natty/partner Translation-en        
Ign http://archive.canonical.com maverick/partner Translation-en_US            
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://archive.canonical.com maverick/partner Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en
Ign http://packages.medibuntu.org natty/non-free Translation-en_US
Ign http://packages.medibuntu.org natty/non-free Translation-en
Fetched 2,618 B in 13s (188 B/s)
W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sun-java-community-team/sun-java6/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```Due to this i cannot download, install, or update anything.

---

### Post by Rasa1111 on 2011-05-09
It seems you have more than one "package manager" running. 
Make sure you dont have synaptic package manager, or software center open when doing this in the terminal. 
If you do, you will get the > E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?message.

Also,
You might want to look into ubuntu restricted extras.

---

