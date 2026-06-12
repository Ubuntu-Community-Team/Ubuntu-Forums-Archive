---
title: "How can I restore my upgrades after I pre-maturely kill my previous update"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by mjsilverstri on 2011-07-24
Hi,

I am using ubuntu 11.04. And I use the update manager to upgrade. But before the update is done, my internet connection is terminated. So I reboot to ubuntu and it said 'i have a partial update'. And I have completed my 'partial update'. But now, I do a 'check for update' again, it said I have no update. Can u please tell me how can I get the rest of my update when I only did a 'partial update' previously?

Thank you.

---

### Post by Old_Grey_Wolf on 2011-07-24
> **mjsilverstri said:**
> Hi,

I am using ubuntu 11.04. And I use the update manager to upgrade. But before the update is done, my internet connection is terminated. So I reboot to ubuntu and it said 'i have a partial update'. And I have completed my 'partial update'. But now, I do a 'check for update' again, it said I have no update. Can u please tell me how can I get the rest of my update when I only did a 'partial update' previously?

Thank you.

Enter the command "sudo apt-get update" in a terminal; then post any errors you get. If you do not get any errors, enter "sudo apt-get dist-upgrade"; then, post any errors you get.

---

### Post by mjsilverstri on 2011-07-24
Thank you. This is the result of both commands:


> ~ $ sudo apt-get update 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty InRelease                                   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,351 B]                            
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release.gpg                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,257 B]                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease                       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty Release                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Hit [http://linux.dropbox.com](http://linux.dropbox.com) natty/main amd64 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg                      
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages                  
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) natty/main Translation-en                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 2,806 B in 10s (265 B/s)                                               
Reading package lists... Done
~ $ sudo apt-get dist-update
E: Invalid operation dist-update
~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~ $ 


---

### Post by Old_Grey_Wolf on 2011-07-25
It looks like you are up-to-date. I don't see where there are any further updates for you.

---

