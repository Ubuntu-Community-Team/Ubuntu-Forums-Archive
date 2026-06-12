---
title: "Trouble Installing Liferea on Xubuntu 12.04"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by user00757322 on 2013-04-10
I'm trying to install liferea rss reader for xubuntu 12.04. I use apt-get, but the process has repeatedly broken down.

apt-get tries to rmdir /usr/share/doc/liferea but fails because "the directory is not empty." I get a message telling me a dpkg error (1) occurred. Liferea will not run.

I'm fairly new to linux. What could be causing this to happen?

---

### Post by fantab on 2013-04-10
Post the output of:

```
sudo apt-get update
```

---

### Post by user00757322 on 2013-04-10
```
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Get:2 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]            
Get:5 http://dl.google.com stable Release.gpg [198 B]                          
Get:6 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Hit http://us.archive.ubuntu.com precise-backports Release                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:7 http://dl.google.com stable Release [1,347 B]                            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://ppa.launchpad.net precise Release.gpg                         
Hit http://ppa.launchpad.net precise Release                             
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Get:8 http://security.ubuntu.com precise-security/main Sources [65.6 kB]       
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Get:9 http://dl.google.com stable/main i386 Packages [1,226 B]                 
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:10 http://us.archive.ubuntu.com precise-updates/main Sources [377 kB]      
Hit http://ppa.launchpad.net precise Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://extras.ubuntu.com precise/main Sources                              
Get:11 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:12 http://security.ubuntu.com precise-security/universe Sources [24.0 kB]  
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,389 B]
Get:14 http://security.ubuntu.com precise-security/main i386 Packages [249 kB] 
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:15 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:16 http://us.archive.ubuntu.com precise-updates/universe Sources [83.4 kB] 
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse Sources [5,475 B]
Get:18 http://us.archive.ubuntu.com precise-updates/main i386 Packages [610 kB]
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:19 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:20 http://security.ubuntu.com precise-security/universe i386 Packages [73.5 kB]
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:21 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,368 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://dl.google.com stable/main Translation-en                            
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://security.ubuntu.com precise-security/main Translation-en            
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:22 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:23 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [196 kB]
Get:24 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [12.4 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources         
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en            
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en      
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en                
Ign http://ppa.launchpad.net precise/main Translation-en_US             
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 1,825 kB in 2s (742 kB/s)
Reading package lists... Done



```

---

### Post by Dennis N on 2013-04-10
Are you trying to install from the liferea PPA? or the Ubuntu repository?

---

### Post by user00757322 on 2013-04-10
I was trying to install from the liferea ppa, but I was having other problems. I ended up upgrading to 12.10. Thanks for the help though. Problem solved.

---

