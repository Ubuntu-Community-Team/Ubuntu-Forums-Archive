---
title: "apt-get update incosistency"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2016-07-09
different time i do *apt-get update* i get a different level of result.

today's result was:

```
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]                          
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                                     
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [248 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [244 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [152 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [149 kB]
Fetched 979 kB in 1s (792 kB/s)                      
Reading package lists... Done
```

yesterday's result was:

```
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]                          
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]                           
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB]       
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [248 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [244 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [152 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [149 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 Packages [608 B]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe i386 Packages [612 B]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe Translation-en [300 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [200 B]
Fetched 1075 kB in 3s (340 kB/s)                                 
Reading package lists... Done
```

3 days ago i got:

```
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]        
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [117 kB]          
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease               
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [114 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [248 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Translation-en [44.8 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [44.0 kB]   
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [50.8 kB]           
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages [33.2 kB]         
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe i386 Packages [33.2 kB]     
Get:13 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe Translation-en [19.9 kB]
Get:14 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [2327 B]   
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [244 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main Translation-en [98.1 kB]                                                        
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [152 kB]                                                     
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [149 kB]                                                      
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe Translation-en [74.9 kB]                                                    
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [69.3 kB]                                             
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [71.0 kB]                                                
Fetched 1755 kB in 13s (134 kB/s)                                                                                                              
Reading package lists... Done
```

and way back on 5 May i got:

```
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [65.9 kB]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [113 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4035 B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [274 kB]        
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [36.2 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5352 B]  
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [154 kB]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2764 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [461 kB] 
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5928 B] 
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [756 kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.0 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [127 kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4982 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [435 kB]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.9 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [359 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12.7 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [127 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13.2 kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [724 kB] 
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [5172 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [253 kB] 
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2570 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3206 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [75.1 kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.6 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [360 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13.6 kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [378 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [7227 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3699 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [188 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Fetched 5083 kB in 22s (223 kB/s)                                              
Reading package lists... Done
```


anyone know what these differences mean?

and yes i have logged so many.

---

### Post by grahammechanical on 2016-07-09
The 5th May result is not relevant. Not because it is for trusty and not xenial but in trusty you had enabled the repositories for the source code and also some PPAs as well as extras which are not enabled in the xenial installation.

I am guessing that the update utility has some way of knowing if a repository has had changes made to the software in the repository. If no changes have been made then there is no point is downloading the list of software in the repository to compare it with the software packages installed on the system to determine which specific packages can be upgraded. 

This might or might not be a new thing for xenial. Certainly things have moved on for Apt in xenial. Although apt-get will still work it is now customary to use apt update and apt upgrade. You can check this out with the command man apt.

Regards

---

### Post by Skaperen on 2016-07-09
i guess my observational fu has degraded with age.  i mixed old logs from 14.04 when i copied over my files after a fresh install of 16.04.  your description makes sense.  i'll mark this as solved.

---

