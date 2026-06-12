---
title: "Partial Upgrade Error"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by Safder on 2011-07-05
Hi,

When I open the Update Manager, I get a prompt for partial upgrade. When I try to go ahead with it, I get an error. Please find it as an attachment.

I tried to look at other threads, but couldn't find the solution to my problem. I wouldn't consider myself as an expert in any sense. So please excuse my ignorance regarding this matter.

Looking forward for help. Thanks.

---

### Post by iansyngin on 2011-07-05
was just going to post the similiar issue.
I don't see the same packages you see though.
mine mentions libreoffice as the package thats failing.
There is approx 330mb of downloads waiting to be installed and i can't do it :(

---

### Post by Safder on 2011-07-05
> **iansyngin said:**
> was just going to post the similiar issue.
I don't see the same packages you see though.
mine mentions libreoffice as the package thats failing.
There is approx 330mb of downloads waiting to be installed and i can't do it :(
The packages shown in my case, are third party packages, but I am not sure where to go from here...

---

### Post by iansyngin on 2011-07-05
> **Safder said:**
> The packages shown in my case, are third party packages, but I am not sure where to go from here...
suppose you could try removing the references to these packages from /etc/apt/sources.list..thats what i'd try anyway

---

### Post by wildmanne39 on 2011-07-06
> **Safder said:**
> The packages shown in my case, are third party packages, but I am not sure where to go from here...Hi, try this in a terminal and see if it helps, if you get different error message post them here, also I partial upgrade is almost always a bad idea.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Safder on 2011-07-06
I ran the commands that you mentioned. The first one ran fine without errors, however after I ran the second command, this is what I got (please note the errors at the end of the run)

```


mmeah@sea-mmeah-linux-v2:~$ sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en                                                                                                                
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_CA                                                                                                             
Hit http://linux.dropbox.com maverick Release                                                                                                                                    
Get:1 http://dl.google.com stable Release.gpg [198B]                                                                                                                             
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                                                            
Hit http://linux.dropbox.com maverick/main amd64 Packages                                                                                                                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA                                                                                                         
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                   
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en                                                                  
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_CA                                                      
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA                                                                   
Hit http://archive.canonical.com maverick Release.gpg                                                                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                               
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA                                                            
Hit http://archive.ubuntu.com maverick Release.gpg                                                                                     
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                           
Hit http://ca.archive.ubuntu.com maverick Release.gpg                                                                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                        
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA                                                                                     
Hit http://deb.opera.com stable Release.gpg                                                                                                                  
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                                                                                               
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_CA                                                                      
Get:3 http://dl.google.com stable Release.gpg [198B]                                                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA                                                                                 
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                   
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en                                                                         
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en_CA                                                             
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                            
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en                                                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_CA                                                              
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                             
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en                                                                                      
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_CA                                                    
Hit http://extras.ubuntu.com maverick Release                                                                                          
Hit http://archive.canonical.com maverick Release                                                                                                            
Hit http://archive.ubuntu.com maverick Release                                                                                                                                   
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                                      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA                                                                                                   
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                                      
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA                                                                                                   
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA                                                                                                     
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg                                                                                                                    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA                                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA                                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA                                                                          
Hit http://security.ubuntu.com maverick-security Release                                                                                                     
Hit http://deb.opera.com stable Release                                                                                                                                          
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en                                                                                    
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en_CA                                                                                 
Get:7 http://ppa.launchpad.net maverick Release [9,771B]                                                                                                                         
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Get:8 http://ppa.launchpad.net maverick Release [57.3kB]                                                                                                                         
Hit http://ppa.launchpad.net maverick Release                                                                                                                                    
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Hit http://extras.ubuntu.com maverick/main Sources                                                                                                                               
Hit http://archive.canonical.com maverick/partner Sources                                                                                                                        
Hit http://archive.ubuntu.com maverick/main Sources                                                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA                                                                             
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                                            
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA                                                                         
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                                          
Get:9 http://ppa.launchpad.net maverick Release [9,739B]                                                                                                     
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Ign http://deb.opera.com stable/non-free amd64 Packages                                                                                                                          
Hit http://extras.ubuntu.com maverick/main amd64 Packages                                                                                                                        
Hit http://archive.canonical.com maverick/partner amd64 Packages                                                                                             
Hit http://archive.ubuntu.com maverick/restricted Sources                                                                                                    
Hit http://ca.archive.ubuntu.com maverick-backports Release.gpg                                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en                                  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA         
Hit http://security.ubuntu.com maverick-security/main Sources                                                    
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                              
Hit http://security.ubuntu.com maverick-security/universe Sources                          
Hit http://security.ubuntu.com maverick-security/main amd64 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages                 
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages                                         
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages                                       
Get:10 http://ppa.launchpad.net maverick Release [9,777B]                                                        
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                         
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex                                  
Ign http://ppa.launchpad.net maverick Release                                                                       
Ign http://deb.opera.com stable/non-free amd64 Packages                                                             
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release                    
Get:11 http://dl.google.com stable Release [1,351B]                                                              
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                   
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex                            
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Hit http://deb.opera.com stable/non-free amd64 Packages                                        
Hit http://ca.archive.ubuntu.com maverick-updates Release                                      
Hit http://ca.archive.ubuntu.com maverick-backports Release                                    
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                   
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex      
Hit http://ppa.launchpad.net maverick/main Sources 
Hit http://ca.archive.ubuntu.com maverick/restricted Sources
Hit http://ca.archive.ubuntu.com maverick/main Sources
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick/universe Sources               
Hit http://ca.archive.ubuntu.com maverick/main amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex             
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex      
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Get:12 http://dl.google.com stable Release [1,347B]                                           
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources                          
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources       
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://ca.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main amd64 Packages            
Get:13 http://dl.google.com stable/main amd64 Packages [1,248B]      
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages                   
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/main Sources     
Hit http://ca.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://ca.archive.ubuntu.com maverick-backports/universe Sources 
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick-backports/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/universe amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main amd64 Packages            
Get:14 http://dl.google.com stable/main amd64 Packages [759B]
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse amd64 Packages
Fetched 6,369B in 1s (3,280B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)


```

Thanks.

---

### Post by wildmanne39 on 2011-07-06
> **Safder said:**
> I ran the commands that you mentioned. The first one ran fine without errors, however after I ran the second command, this is what I got (please note the errors at the end of the run)

```


mmeah@sea-mmeah-linux-v2:~$ sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en                                                                                                                
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_CA                                                                                                             
Hit http://linux.dropbox.com maverick Release                                                                                                                                    
Get:1 http://dl.google.com stable Release.gpg [198B]                                                                                                                             
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en                                                                                                            
Hit http://linux.dropbox.com maverick/main amd64 Packages                                                                                                                        
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_CA                                                                                                         
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                   
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en                                                                  
Ign http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/ maverick/main Translation-en_CA                                                      
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_CA                                                                   
Hit http://archive.canonical.com maverick Release.gpg                                                                                  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                               
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_CA                                                            
Hit http://archive.ubuntu.com maverick Release.gpg                                                                                     
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                           
Hit http://ca.archive.ubuntu.com maverick Release.gpg                                                                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_CA                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                        
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_CA                                                                                     
Hit http://deb.opera.com stable Release.gpg                                                                                                                  
Ign http://deb.opera.com/opera/ stable/non-free Translation-en                                                                                               
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_CA                                                                      
Get:3 http://dl.google.com stable Release.gpg [198B]                                                                                   
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en                                                                                                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_CA                                                                                 
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                   
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en                                                                         
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en_CA                                                             
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                            
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en                                                                 
Ign http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ maverick/main Translation-en_CA                                                              
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                             
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en                                                                                      
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_CA                                                    
Hit http://extras.ubuntu.com maverick Release                                                                                          
Hit http://archive.canonical.com maverick Release                                                                                                            
Hit http://archive.ubuntu.com maverick Release                                                                                                                                   
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]                                                                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                                      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_CA                                                                                                   
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                                      
Hit http://ca.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_CA                                                                                                   
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_CA                                                                                                     
Hit http://ca.archive.ubuntu.com maverick-updates Release.gpg                                                                                                                    
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_CA                                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_CA                                                                        
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_CA                                                                          
Hit http://security.ubuntu.com maverick-security Release                                                                                                     
Hit http://deb.opera.com stable Release                                                                                                                                          
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en                                                                                    
Ign http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu/ maverick/main Translation-en_CA                                                                                 
Get:7 http://ppa.launchpad.net maverick Release [9,771B]                                                                                                                         
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Get:8 http://ppa.launchpad.net maverick Release [57.3kB]                                                                                                                         
Hit http://ppa.launchpad.net maverick Release                                                                                                                                    
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Hit http://extras.ubuntu.com maverick/main Sources                                                                                                                               
Hit http://archive.canonical.com maverick/partner Sources                                                                                                                        
Hit http://archive.ubuntu.com maverick/main Sources                                                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_CA                                                                             
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_CA                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                                          
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_CA                                                                       
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                                            
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_CA                                                                         
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                                          
Get:9 http://ppa.launchpad.net maverick Release [9,739B]                                                                                                     
Ign http://ppa.launchpad.net maverick Release                                                                                                                                    
Ign http://deb.opera.com stable/non-free amd64 Packages                                                                                                                          
Hit http://extras.ubuntu.com maverick/main amd64 Packages                                                                                                                        
Hit http://archive.canonical.com maverick/partner amd64 Packages                                                                                             
Hit http://archive.ubuntu.com maverick/restricted Sources                                                                                                    
Hit http://ca.archive.ubuntu.com maverick-backports Release.gpg                                                                        
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en                                  
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_CA         
Hit http://security.ubuntu.com maverick-security/main Sources                                                    
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                              
Hit http://security.ubuntu.com maverick-security/universe Sources                          
Hit http://security.ubuntu.com maverick-security/main amd64 Packages                       
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages                 
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages                                         
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages                                       
Get:10 http://ppa.launchpad.net maverick Release [9,777B]                                                        
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                         
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex                                  
Ign http://ppa.launchpad.net maverick Release                                                                       
Ign http://deb.opera.com stable/non-free amd64 Packages                                                             
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en      
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com maverick Release                    
Get:11 http://dl.google.com stable Release [1,351B]                                                              
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                   
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex                            
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Hit http://deb.opera.com stable/non-free amd64 Packages                                        
Hit http://ca.archive.ubuntu.com maverick-updates Release                                      
Hit http://ca.archive.ubuntu.com maverick-backports Release                                    
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                                   
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex      
Hit http://ppa.launchpad.net maverick/main Sources 
Hit http://ca.archive.ubuntu.com maverick/restricted Sources
Hit http://ca.archive.ubuntu.com maverick/main Sources
Hit http://ca.archive.ubuntu.com maverick/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick/universe Sources               
Hit http://ca.archive.ubuntu.com maverick/main amd64 Packages            
Hit http://ca.archive.ubuntu.com maverick/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/universe amd64 Packages
Hit http://ca.archive.ubuntu.com maverick/multiverse amd64 Packages      
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex             
Ign http://ppa.launchpad.net maverick/main amd64 Packages/DiffIndex      
Hit http://ppa.launchpad.net maverick/main Sources                       
Hit http://ppa.launchpad.net maverick/main amd64 Packages                
Get:12 http://dl.google.com stable Release [1,347B]                                           
Hit http://ca.archive.ubuntu.com maverick-updates/restricted Sources                          
Hit http://ca.archive.ubuntu.com maverick-updates/main Sources       
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://ca.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://ca.archive.ubuntu.com maverick-updates/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-updates/restricted amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main amd64 Packages            
Get:13 http://dl.google.com stable/main amd64 Packages [1,248B]      
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages                   
Hit http://ca.archive.ubuntu.com maverick-updates/multiverse amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/main Sources     
Hit http://ca.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://ca.archive.ubuntu.com maverick-backports/universe Sources 
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com maverick-backports/main amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/restricted amd64 Packages
Hit http://ca.archive.ubuntu.com maverick-backports/universe amd64 Packages
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main amd64 Packages            
Get:14 http://dl.google.com stable/main amd64 Packages [759B]
Hit http://ca.archive.ubuntu.com maverick-backports/multiverse amd64 Packages
Fetched 6,369B in 1s (3,280B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)


```

Thanks.
>  Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)
This is because there are two of the same ppa in the source list, go into synaptic, click on settings, repositories, other software and look for two of the same ppas and uncheck one of them or remove it completely.
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E091672E206FF0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1FFD34C9EB13C954
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211
This error is because there is no key, that means it will not get the updates because without the key there is no way to verify if the ppa is safe to use. In the window where other software is located, in synaptic, there is a tab called Authentication, you can add the public key there if you can find  it, if you added the ppas yourself you will need to go to the site you added them from and get the key and add it or uncheck the ppas. It looks like these were installed as official ppas, it is possible that the key got corrupted, I have been looking for the key so you can add it, but I have not found the key so far,also you have a big source list and some of them look strange to me. You may want to clean it up in synaptic.
I found this link that talks about key errors.
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by Safder on 2011-07-08
After, I imported all the public keys, I was able to resolve the error and as a result complte the "partial upgrade". Thanks a lot for your help :)

---

### Post by gerence13 on 2013-02-27
> **Wild Man said:**
> Hi, try this in a terminal and see if it helps, if you get different error message post them here, also I partial upgrade is almost always a bad idea.
```
sudo rm /var/lib/apt/lists/* -vf
```Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
I did what you instruct but mine still has errors...



TERMINAL (after the instructions)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-proposed/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



can you pls help me with this..? 

I just forgotten about a month of updating and then this problem just emerge. I'm a new user of ubuntu so pls help me..

Im using Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010 and supported until April 2013.
    
Thank you

---

