---
title: "No upgrades in Natty since three days?"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by tnf on 2011-05-16
Hello,

I upgraded to Natty three days ago but didn't get any updates since. I think there is a problem as I assume that there have been updates in Natty in the last three days?

apt-get update gives me

```
apt-get update
Hit http://packages.medibuntu.org natty InRelease
Ign http://dl.google.com testing InRelease                                                                                                                                                    
Ign http://ppa.launchpad.net natty InRelease                                                                                                                                                  
Ign http://ppa.launchpad.net natty InRelease                                                                                                                                                  
Ign http://ppa.launchpad.net natty InRelease                                                                                                                                                  
Ign http://extras.ubuntu.com natty InRelease                                                                                                                                                     
Ign http://de.archive.ubuntu.com natty InRelease                                                                                                                                                 
Ign http://archive.canonical.com natty InRelease                                                                                                                                                               
Ign http://ppa.launchpad.net natty InRelease                                                                                                                                                                   
Hit http://ppa.launchpad.net natty Release.gpg                                                                                                                                                                 
Hit http://ppa.launchpad.net natty Release.gpg                                                                                                                                                                 
Ign http://de.archive.ubuntu.com natty-updates InRelease                                                                                                                                                       
Hit http://extras.ubuntu.com natty Release.gpg                                                                                                                                                 
Ign http://de.archive.ubuntu.com natty-proposed InRelease                                                                                                                                      
Hit http://packages.medibuntu.org natty/free amd64 Packages                                                                                                                                    
Get:1 http://dl.google.com testing Release.gpg [189 B]                                                                                                                                         
Hit http://ppa.launchpad.net natty Release.gpg                                                                                                                                                                 
Hit http://archive.canonical.com natty Release.gpg                                                                                                                                                             
Hit http://extras.ubuntu.com natty Release                                                                                                                                                                     
Hit http://de.archive.ubuntu.com natty Release.gpg                                                                                                                                                             
Hit http://ppa.launchpad.net natty Release.gpg                                                                                                                                                                 
Hit http://ppa.launchpad.net natty Release                                                                                                                                                                     
Ign http://security.ubuntu.com natty-security InRelease                                                                                                                                                        
Hit http://packages.medibuntu.org natty/non-free amd64 Packages                                                                                                                                
Hit http://archive.canonical.com natty Release                                                                                                                                                                 
Hit http://de.archive.ubuntu.com natty-updates Release.gpg                                                                                                                                                     
Hit http://extras.ubuntu.com natty/main amd64 Packages                                                                                                                                                         
Hit http://ppa.launchpad.net natty Release                                                                                                                                                                     
Get:2 http://dl.google.com testing Release [2513 B]                                                                                                                                                            
Ign http://packages.medibuntu.org natty/free TranslationIndex                                                                                                                                                  
Hit http://security.ubuntu.com natty-security Release.gpg                                                                                                                                     
Hit http://ppa.launchpad.net natty Release                                                                                                                                                    
Hit http://ppa.launchpad.net natty Release                                                                                                                                                                     
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                                                                                                                       
Hit http://archive.canonical.com natty/partner amd64 Packages                                                                                                                                                  
Hit http://de.archive.ubuntu.com natty-proposed Release.gpg                                                                                                                                                    
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                                                                                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                                                                      
Get:3 http://dl.google.com testing/non-free amd64 Packages [786 B]                                                                                                                 
Hit http://security.ubuntu.com natty-security Release                                                                                                                                  
Ign http://packages.medibuntu.org natty/non-free TranslationIndex                                                                                                                       
Ign http://archive.canonical.com natty/partner TranslationIndex                                                                                                                         
Hit http://de.archive.ubuntu.com natty Release                                                                                                                                                     
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                                                                                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                                                                                       
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                                                                                         
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                                                           
Hit http://ppa.launchpad.net natty/main Sources                                                                                                                                    
Hit http://ppa.launchpad.net natty/main amd64 Packages                                                                                                                             
Ign http://ppa.launchpad.net natty/main TranslationIndex                                                                                                                           
Hit http://security.ubuntu.com natty-security/main amd64 Packages                                                                                                                  
Hit http://de.archive.ubuntu.com natty-updates Release                                                                                                                                        
Ign http://dl.google.com testing/non-free TranslationIndex                                                                                                                                                     
Ign http://download.virtualbox.org natty InRelease                                                                                                                                                             
Hit http://de.archive.ubuntu.com natty-proposed Release                                                                                                                                       
Hit http://security.ubuntu.com natty-security/restricted amd64 Packages                                                                                                                                        
Hit http://security.ubuntu.com natty-security/universe amd64 Packages                                                                                                                                          
Hit http://security.ubuntu.com natty-security/multiverse amd64 Packages                                                                                                                                        
Ign http://security.ubuntu.com natty-security/main TranslationIndex                                                                                                                                            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex                                                                                                                                      
Hit http://de.archive.ubuntu.com natty/main amd64 Packages                                                                                                                                                     
Hit http://de.archive.ubuntu.com natty/restricted amd64 Packages                                                                                                                                               
Hit http://de.archive.ubuntu.com natty/universe amd64 Packages                                                                                                                                                 
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex                                                                                                                                      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex                                                                                                                                        
Hit http://de.archive.ubuntu.com natty/multiverse amd64 Packages                                                                                                                                               
Ign http://de.archive.ubuntu.com natty/main TranslationIndex                                                                                                                                                   
Ign http://de.archive.ubuntu.com natty/multiverse TranslationIndex                                                                                                                            
Ign http://de.archive.ubuntu.com natty/restricted TranslationIndex                                                                                                                            
Ign http://de.archive.ubuntu.com natty/universe TranslationIndex                                                                                                                              
Hit http://download.virtualbox.org natty Release.gpg                                                                                                                               
Hit http://de.archive.ubuntu.com natty-updates/main amd64 Packages                                                                                                                 
Ign http://extras.ubuntu.com natty/main Translation-en                                                                                                                                        
Hit http://de.archive.ubuntu.com natty-updates/restricted amd64 Packages                                                                                                                      
Hit http://de.archive.ubuntu.com natty-updates/universe amd64 Packages                                                                                       
Ign http://extras.ubuntu.com natty/main Translation-de                                                                                                                                                         
Hit http://de.archive.ubuntu.com natty-updates/multiverse amd64 Packages                                                                                                                                       
Ign http://de.archive.ubuntu.com natty-updates/main TranslationIndex                                                                                                                          
Ign http://de.archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                                                                                    
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                                                        
Ign http://ppa.launchpad.net natty/main Translation-de                                                                                                                                        
Ign http://de.archive.ubuntu.com natty-updates/restricted TranslationIndex                                                             
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                 
Ign http://ppa.launchpad.net natty/main Translation-de                                                                                                                  
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                                  
Ign http://de.archive.ubuntu.com natty-updates/universe TranslationIndex                                                                                                                      
Ign http://archive.canonical.com natty/partner Translation-en                                                                                                                                 
Hit http://de.archive.ubuntu.com natty-proposed/restricted amd64 Packages                                                                                               
Hit http://download.virtualbox.org natty Release                                                                                                             
Ign http://ppa.launchpad.net natty/main Translation-de                                                                                                       
Ign http://ppa.launchpad.net natty/main Translation-en                                                                                                       
Ign http://ppa.launchpad.net natty/main Translation-de                                                                                                       
Hit http://de.archive.ubuntu.com natty-proposed/main amd64 Packages                                                                    
Ign http://archive.canonical.com natty/partner Translation-de                                                                                     
Hit http://de.archive.ubuntu.com natty-proposed/multiverse amd64 Packages                                                                         
Hit http://de.archive.ubuntu.com natty-proposed/universe amd64 Packages                                                                           
Ign http://de.archive.ubuntu.com natty-proposed/main TranslationIndex                                                                             
Ign http://de.archive.ubuntu.com natty-proposed/multiverse TranslationIndex                                                                       
Ign http://de.archive.ubuntu.com natty-proposed/restricted TranslationIndex                                                 
Ign http://de.archive.ubuntu.com natty-proposed/universe TranslationIndex                  
Hit http://de.archive.ubuntu.com natty/main Translation-de                                                                  
Ign http://security.ubuntu.com natty-security/main Translation-en                                                           
Ign http://security.ubuntu.com natty-security/main Translation-de                                                
Hit http://de.archive.ubuntu.com natty/multiverse Translation-de                                                 
Hit http://download.virtualbox.org natty/contrib amd64 Packages                                                             
Hit http://de.archive.ubuntu.com natty/restricted Translation-de                                                            
Ign http://security.ubuntu.com natty-security/multiverse Translation-en                                                     
Ign http://security.ubuntu.com natty-security/multiverse Translation-de                    
Ign http://security.ubuntu.com natty-security/restricted Translation-en                    
Hit http://de.archive.ubuntu.com natty/universe Translation-de                             
Ign http://security.ubuntu.com natty-security/restricted Translation-de                                          
Ign http://security.ubuntu.com natty-security/universe Translation-en                                            
Ign http://security.ubuntu.com natty-security/universe Translation-de                      
Ign http://download.virtualbox.org natty/contrib TranslationIndex                          
Ign http://packages.medibuntu.org natty/free Translation-en                                           
Ign http://packages.medibuntu.org natty/free Translation-de                                           
Ign http://packages.medibuntu.org natty/non-free Translation-en      
Ign http://packages.medibuntu.org natty/non-free Translation-de      
Ign http://de.archive.ubuntu.com natty/main Translation-en           
Ign http://de.archive.ubuntu.com natty/multiverse Translation-en     
Ign http://de.archive.ubuntu.com natty/restricted Translation-en
Ign http://de.archive.ubuntu.com natty/universe Translation-en       
Ign http://de.archive.ubuntu.com natty-updates/main Translation-en   
Ign http://de.archive.ubuntu.com natty-updates/main Translation-de
Ign http://de.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://de.archive.ubuntu.com natty-updates/multiverse Translation-de
Ign http://de.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://de.archive.ubuntu.com natty-updates/restricted Translation-de
Ign http://de.archive.ubuntu.com natty-updates/universe Translation-en
Ign http://de.archive.ubuntu.com natty-updates/universe Translation-de
Ign http://de.archive.ubuntu.com natty-proposed/main Translation-en  
Ign http://de.archive.ubuntu.com natty-proposed/main Translation-de
Ign http://de.archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://de.archive.ubuntu.com natty-proposed/multiverse Translation-de
Ign http://de.archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://de.archive.ubuntu.com natty-proposed/restricted Translation-de
Ign http://de.archive.ubuntu.com natty-proposed/universe Translation-en
Ign http://de.archive.ubuntu.com natty-proposed/universe Translation-de
Ign http://download.virtualbox.org natty/contrib Translation-en
Ign http://download.virtualbox.org natty/contrib Translation-de
Ign http://dl.google.com testing/non-free Translation-en
Ign http://dl.google.com testing/non-free Translation-de
Fetched 3488 B in 3s (1003 B/s)
Reading package lists... Done
```

and then apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
```

Any ideas what might be wrong?

---

### Post by edcv on 2011-05-16
I'm having the same "problem", not sure if it is a problem though.

---

### Post by tnf on 2011-05-16
Oh, so there actually aren't any updates in Natty? Couldn't believe this with such a short period since the release

---

### Post by eggi-j on 2011-05-16
I've got the same problem or "not problem". No updates for at least a week. Upgraded from 10.10, and got all of those ign repositories.

So, is this something to worry about?

---

### Post by howefield on 2011-05-16
Could be to do with the Ubuntu Developer Summit last week in Budapest, I'd expect updates to start rolling in soon enough.

---

