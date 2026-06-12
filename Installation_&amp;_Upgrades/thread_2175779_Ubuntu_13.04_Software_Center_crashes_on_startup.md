---
title: "Ubuntu 13.04 Software Center crashes on startup"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by TimothyLinux on 2013-09-21
Hello! I'm a newbie in Ubuntu and I have a big problem. For some reason, the software center crashes on startup. I thought it was because of un updated packages, so I did sudo apt-get update and it did this:```
Hit http://dl.google.com stable Release.gpg
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://security.ubuntu.com raring-security Release.gpg                     
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://ppa.launchpad.net raring Release.gpg                                
Get:1 https://download.01.org Ubuntu Release.gpg [836 B]                       
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                  
Hit https://download.01.org Ubuntu Release                                     
Ign https://download.01.org Ubuntu Release                                     
Hit http://security.ubuntu.com raring-security Release                         
Ign https://download.01.org Ubuntu/13.04 i386 Packages/DiffIndex               
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://deb.opera.com stable Release                                        
Hit http://security.ubuntu.com raring-security/main Sources                    
Hit http://us.archive.ubuntu.com raring-updates Release                        
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://us.archive.ubuntu.com raring-backports Release                      
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/universe Sources                
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/multiverse Sources    
Hit http://us.archive.ubuntu.com raring/multiverse Sources           
Hit http://security.ubuntu.com raring-security/main i386 Packages    
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit https://private-ppa.launchpad.net raring Release.gpg             
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://security.ubuntu.com raring-security/restricted i386 Packages
Hit http://ppa.launchpad.net raring Release.gpg                      
Hit https://private-ppa.launchpad.net raring Release.gpg             
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Hit http://security.ubuntu.com raring-security/universe i386 Packages          
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages     
Hit https://private-ppa.launchpad.net raring Release                 
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/multiverse i386 Packages        
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Hit https://private-ppa.launchpad.net raring Release                 
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit https://private-ppa.launchpad.net raring/main i386 Packages                
Hit http://ppa.launchpad.net raring Release.gpg                                
Hit http://security.ubuntu.com raring-security/main Translation-en             
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en    
Hit http://ppa.launchpad.net raring Release                          
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Hit http://ppa.launchpad.net raring Release                                    
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Hit http://ppa.launchpad.net raring Release                                    
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Hit http://us.archive.ubuntu.com raring/universe Translation-en                
Hit http://security.ubuntu.com raring-security/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/main Sources         
Hit http://ppa.launchpad.net raring Release                          
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://ppa.launchpad.net raring Release                          
Hit http://us.archive.ubuntu.com raring-updates/universe Sources               
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources   
Hit http://ppa.launchpad.net raring Release    
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages             
Hit http://security.ubuntu.com raring-security/universe Translation-en
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages
Hit http://ppa.launchpad.net raring Release    
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en            
Hit http://ppa.launchpad.net raring Release                          
Hit https://private-ppa.launchpad.net raring/main i386 Packages                
Hit http://ppa.launchpad.net raring Release                          
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en      
Hit http://ppa.launchpad.net raring Release                          
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en
Hit http://us.archive.ubuntu.com raring-backports/main Sources
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources
Hit http://ppa.launchpad.net raring/main i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/universe Sources
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Ign http://security.ubuntu.com raring-security/main Translation-en_US
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit http://ppa.launchpad.net raring/main i386 Packages
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en          
Hit https://download.01.org Ubuntu/13.04 i386 Packages                         
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Ign https://download.01.org Ubuntu/13.04 Translation-en_US                     
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign https://download.01.org Ubuntu/13.04 Translation-en                        
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en      
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Hit http://ppa.launchpad.net raring/main i386 Packages                         
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Ign http://ppa.launchpad.net raring/main Translation-en_US
Ign http://ppa.launchpad.net raring/main Translation-en
Fetched 836 B in 28s (29 B/s)
Reading package lists... Done
W: GPG error: https://download.01.org Ubuntu Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66


```

Is there anything I can do to fix this? Thx in advance!

---

### Post by sanderj on 2013-09-21
Software Center should not crash, but I would start by getting the "sudo apt-get update" correctly functioning.

I would start by removing [https://download.01.org](https://download.01.org) from your sources list: check /etc/apt/sources.list and the directory /etc/apt/sources.list.d/ ... you should find it there. Can you remove it, and then run "sudo apt-get update" without errors?

---

