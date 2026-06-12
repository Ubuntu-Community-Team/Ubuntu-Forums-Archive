---
title: "Ubuntu 14.04 upgrade gives 403 forbidden error"
date: 2017-01-05
forum: Installation &amp; Upgrades
---

### Post by aloktiwari on 2017-01-05
** How i resolve these error below :- i run command => sudo apt-get update**

```
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates Release.gpg                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports Release.gpg                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty Release                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates Release                        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports Release                      
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.5 kB]                      
Ign [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0 InRelease                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Get:2 [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0 Release.gpg [455 B]       
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [65.9 kB]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease                                 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg [933 B]                  
Get:5 [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0 Release [3,462 B]         
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.5 kB]                      
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist InRelease                         
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg [933 B]                     
Get:9 [http://dl.google.com](http://dl.google.com) stable Release.gpg [916 B]                          
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Sources                     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Sources                     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Sources                           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Sources                       
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main amd64 Packages                    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted amd64 Packages              
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe amd64 Packages                
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse amd64 Packages              
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main i386 Packages                     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted i386 Packages               
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe i386 Packages                 
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse i386 Packages               
  403  Forbidden
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en_IN                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/main Translation-en                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/multiverse Translation-en              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/restricted Translation-en              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty/universe Translation-en                
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Sources                   
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Sources               
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main amd64 Packages            
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
  403  Forbidden
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [3,199 B] 
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main i386 Packages             
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe i386 Packages         
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse i386 Packages       
  403  Forbidden
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Translation-en_IN     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-updates/universe Translation-en        
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Sources                 
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Sources           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Sources           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main amd64 Packages          
  403  Forbidden
Get:11 [http://dl.google.com](http://dl.google.com) stable Release.gpg [916 B]                         
Get:12 [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0/multiverse amd64 Packages [10.7 kB]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main i386 Packages           
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe i386 Packages       
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
  403  Forbidden
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/main Translation-en          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) trusty-backports/universe Translation-en      
Get:13 [http://archive.canonical.com](http://archive.canonical.com) trusty Release [9,359 B]                   
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]                       
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15.5 kB]                     
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release [58.5 kB]                      
Get:17 [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0/multiverse i386 Packages [29 B]
Get:18 [http://dl.google.com](http://dl.google.com) stable Release [1,189 B]                           
Get:19 [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release.gpg [490 B]            
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4,613 B] 
Get:21 [http://dl.google.com](http://dl.google.com) stable Release [2,141 B]                           
Get:22 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages [5,494 B]    
Get:23 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]                     
Get:24 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [2,181 B]           
Get:25 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,420 B]               
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources [1,064 kB]                
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [123 kB]        
Get:28 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages [6,205 B]     
Get:29 [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release [2,040 B]              
Get:30 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages [14 B]              
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [2,205 B]            
Get:32 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [778 B]                 
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources [5,433 B]           
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [46.5 kB]   
Get:35 [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en [4,593 B]    
Get:36 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]               
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [898 B]             
Ign [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0/multiverse Translation-en_IN
Get:38 [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen amd64 Packages [29.8 kB] 
Get:39 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [784 B]                  
Ign [http://repo.mongodb.org](http://repo.mongodb.org) trusty/mongodb-org/3.0/multiverse Translation-en   
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [570 kB] 
Get:41 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [44.6 kB]           
Get:42 [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen i386 Packages [29.6 kB]  
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13.3 kB]
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [44.6 kB]            
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [146 kB]
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [25.6 kB]           
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4,140 B]
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [3,389 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_IN                     
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [529 kB]  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [3,389 B]            
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [13.1 kB]
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [1,556 B]           
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [147 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4,301 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:55 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [314 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:56 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [2,201 B]
Get:57 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [3,349 B]
Get:58 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [86.6 kB]
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en_IN           
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en              
Fetched 3,504 kB in 7s (483 kB/s)                                              
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by wildmanne39 on 2017-01-05
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by aloktiwari on 2017-01-05
[COLOR=#000000]```

[/COLOR]Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty InRelease
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates InRelease                      
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports InRelease                    
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty Release.gpg                            
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates Release.gpg                    
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports Release.gpg                  
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty Release                                
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates Release                        
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports Release                      
Get:1 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease [15.5 kB]                      
Ign [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0 InRelease                   
Ign [http://dl.google.com]("http://dl.google.com/") stable InRelease                                      
Ign [http://archive.canonical.com]("http://archive.canonical.com/") trusty InRelease                              
Get:2 [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0 Release.gpg [455 B]       
Get:3 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security InRelease [65.9 kB]           
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty InRelease                                  
Ign [http://archive.ubuntu.com]("http://archive.ubuntu.com/") trusty InRelease                                 
Ign [http://dl.google.com]("http://dl.google.com/") stable InRelease                                      
Get:4 [http://archive.canonical.com]("http://archive.canonical.com/") trusty Release.gpg [933 B]                  
Get:5 [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0 Release [3,462 B]         
Get:6 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty Release.gpg [72 B]                       
Get:7 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease [15.5 kB]                      
Ign [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist InRelease                         
Get:8 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") trusty Release.gpg [933 B]                     
Get:9 [http://dl.google.com]("http://dl.google.com/") stable Release.gpg [916 B]                          
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/multiverse Sources                     
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/restricted Sources                     
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/main Sources                           
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/universe Sources                       
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/main amd64 Packages                    
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/restricted amd64 Packages              
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/universe amd64 Packages                
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/multiverse amd64 Packages              
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/main i386 Packages                     
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/restricted i386 Packages               
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/universe i386 Packages                 
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/multiverse i386 Packages               
  403  Forbidden
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/main Translation-en_IN                 
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/main Translation-en                    
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/multiverse Translation-en_IN           
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/multiverse Translation-en              
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/restricted Translation-en_IN           
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/restricted Translation-en              
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty/universe Translation-en                
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/multiverse Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/restricted Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/main Sources                   
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/universe Sources               
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/main amd64 Packages            
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/restricted amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/universe amd64 Packages        
  403  Forbidden
Get:10 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/multiverse Sources [3,199 B] 
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/multiverse amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/main i386 Packages             
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/restricted i386 Packages       
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/universe i386 Packages         
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/multiverse i386 Packages       
  403  Forbidden
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/main Translation-en            
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/multiverse Translation-en_IN   
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/multiverse Translation-en      
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/restricted Translation-en      
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/universe Translation-en_IN     
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-updates/universe Translation-en        
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/main Sources                 
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/restricted Sources           
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/universe Sources             
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/multiverse Sources           
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/main amd64 Packages          
  403  Forbidden
Get:11 [http://dl.google.com]("http://dl.google.com/") stable Release.gpg [916 B]                         
Get:12 [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0/multiverse amd64 Packages [10.7 kB]
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/restricted amd64 Packages    
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/universe amd64 Packages      
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/multiverse amd64 Packages    
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/main i386 Packages           
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/restricted i386 Packages     
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/universe i386 Packages       
  403  Forbidden
Err [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/multiverse i386 Packages     
  403  Forbidden
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/main Translation-en_IN       
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/main Translation-en          
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/multiverse Translation-en_IN 
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/multiverse Translation-en    
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/restricted Translation-en_IN 
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/restricted Translation-en    
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/universe Translation-en_IN   
Ign [http://in.archive.ubuntu.com]("http://in.archive.ubuntu.com/") trusty-backports/universe Translation-en      
Get:13 [http://archive.canonical.com]("http://archive.canonical.com/") trusty Release [9,359 B]                   
Get:14 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty Release [11.9 kB]                       
Get:15 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty InRelease [15.5 kB]                     
Get:16 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") trusty Release [58.5 kB]                      
Get:17 [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0/multiverse i386 Packages [29 B]
Get:18 [http://dl.google.com]("http://dl.google.com/") stable Release [1,189 B]                           
Get:19 [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist Release.gpg [490 B]            
Get:20 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/restricted Sources [4,613 B] 
Get:21 [http://dl.google.com]("http://dl.google.com/") stable Release [2,141 B]                           
Get:22 [http://archive.canonical.com]("http://archive.canonical.com/") trusty/partner amd64 Packages [5,494 B]    
Get:23 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty/main Sources [14 B]                     
Get:24 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages [2,181 B]           
Get:25 [http://dl.google.com]("http://dl.google.com/") stable/main amd64 Packages [1,420 B]               
Get:26 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") trusty/main Sources [1,064 kB]                
Get:27 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/main Sources [123 kB]        
Get:28 [http://archive.canonical.com]("http://archive.canonical.com/") trusty/partner i386 Packages [6,205 B]     
Get:29 [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist Release [2,040 B]              
Get:30 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty/main amd64 Packages [14 B]              
Get:31 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages [2,205 B]            
Get:32 [http://dl.google.com]("http://dl.google.com/") stable/main amd64 Packages [778 B]                 
Get:33 [http://archive.ubuntu.com]("http://archive.ubuntu.com/") trusty/restricted Sources [5,433 B]           
Get:34 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/universe Sources [46.5 kB]   
Get:35 [http://archive.canonical.com]("http://archive.canonical.com/") trusty/partner Translation-en [4,593 B]    
Get:36 [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty/main i386 Packages [14 B]               
Get:37 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en [898 B]             
Ign [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0/multiverse Translation-en_IN
Get:38 [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist/10gen amd64 Packages [29.8 kB] 
Get:39 [http://dl.google.com]("http://dl.google.com/") stable/main i386 Packages [784 B]                  
Ign [http://repo.mongodb.org]("http://repo.mongodb.org/") trusty/mongodb-org/3.0/multiverse Translation-en   
Get:40 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/main amd64 Packages [570 kB] 
Get:41 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages [44.6 kB]           
Get:42 [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist/10gen i386 Packages [29.6 kB]  
Get:43 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/restricted amd64 Packages [13.3 kB]
Get:44 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages [44.6 kB]            
Get:45 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/universe amd64 Packages [146 kB]
Get:46 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en [25.6 kB]           
Get:47 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/multiverse amd64 Packages [4,140 B]
Get:48 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main amd64 Packages [3,389 B]           
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty/main Translation-en_IN                     
Get:49 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/main i386 Packages [529 kB]  
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") trusty/main Translation-en                        
Get:50 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main i386 Packages [3,389 B]            
Get:51 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/restricted i386 Packages [13.1 kB]
Get:52 [http://ppa.launchpad.net]("http://ppa.launchpad.net/") trusty/main Translation-en [1,556 B]           
Get:53 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/universe i386 Packages [147 kB]
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en_IN                         
Get:54 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/multiverse i386 Packages [4,301 B]
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en                            
Get:55 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/main Translation-en [314 kB]
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en_IN                         
Ign [http://dl.google.com]("http://dl.google.com/") stable/main Translation-en                            
Get:56 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/multiverse Translation-en [2,201 B]
Get:57 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/restricted Translation-en [3,349 B]
Get:58 [http://security.ubuntu.com]("http://security.ubuntu.com/") trusty-security/universe Translation-en [86.6 kB]
Ign [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist/10gen Translation-en_IN           
Ign [http://downloads-distro.mongodb.org]("http://downloads-distro.mongodb.org/") dist/10gen Translation-en              
Fetched 3,504 kB in 7s (483 kB/s)                                              
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...source/Sources]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...amd64/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages")  403  Forbidden


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/...-i386/Packages]("http://in.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages")  403  Forbidden


E: Some index files failed to download. They have been ignored, or old ones used instead.[COLOR=#000000]
```[/COLOR]

---

