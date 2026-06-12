---
title: "E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_*"
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by chetkgp on 2012-10-26
Dear All,

I am trying to do a update on my Ubuntu 11.10 and get the following
error.
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index (1)

I have tried several things like
1. the solution from [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/207473](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/207473)

2. Removing /var/lib/apt/lists/partial

3. Removing /var/lib/apt/lists

4. Changing the sever

... but none of them have worked. Any pointers as to how this problem can be solved.

The entire output of apt-get update is shown below.

sharon@deltadawn:/home/sharon$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                 
Ign [http://c.archive.ubuntu.com](http://c.archive.ubuntu.com) oneiric InRelease                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports InRelease             
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                        
Get:2 [http://c.archive.ubuntu.com](http://c.archive.ubuntu.com) oneiric Release.gpg [198 B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                   
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security InRelease               
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick InRelease                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease                  
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [764 B]              
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release.gpg [198 B] 
Get:6 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]            
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]               
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release.gpg [198 B]   
Get:9 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198 B]           
Get:10 [http://c.archive.ubuntu.com](http://c.archive.ubuntu.com) oneiric Release [40.8 kB]              
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]     
Get:13 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]             
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports Release [39.8 kB]  
Get:15 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925 B]            
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                
Get:17 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,944 B]
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release [49.6 kB]    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex         
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main Sources [6,938 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]        
Get:21 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,856 B]    
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted Sources [14 B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_IN                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                       
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]       
Get:24 [http://c.archive.ubuntu.com](http://c.archive.ubuntu.com) oneiric/main Sources [877 kB]          
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe Sources [10.8 kB]
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse Sources [14 B]
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main i386 Packages [14.9 kB]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                         
  503  Service Unavailable
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted i386 Packages [14 B]
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                   
  503  Service Unavailable
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_IN        
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe i386 Packages [23.7 kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en           
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse i386 Packages [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main TranslationIndex 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe TranslationIndex
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/main Sources [50.6 kB]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:34 [http://c.archive.ubuntu.com](http://c.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [2,676 B]     
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5,470 B]       
38% [35 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [2,596 B]     
38% [37 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [2,922 B]     
38% [38 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [3bzip2: (stdin) is not a bzip2 file.
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/main i386 Packages [184 kB]
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [181 kB]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [60.7 kB] 
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [4,395 B]
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [4,745 B]  
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/main Translation-en [87.1 kB]
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security/restricted Translation-en [978 B]
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex [423 kB]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [151 kB]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex [8,218 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [9,930 B]   
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [3,564 B]
51% [53 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [2,605 B]
52% [54 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [2,461 B]
52% [55 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [2,850 B]
53% [56 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [3bzip2: (stdin) is not a bzip2 file.
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [14.5 kB]
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [1,379 B]
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [48.7 kB]
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [2,357 B]
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [73 B]
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [5,306 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [188 kB]
60% [64 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [4,174 B]
60% [65 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [34bzip2: (stdin) is not a bzip2 file.
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/main Translation-en   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/restricted Translation-en
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [1,641 kB]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-backports/universe Translation-en
75% [66 Packages bzip2 0 B] [Waiting for headers] [34 Sources 2,801 kB/4,6bzip2: (stdin) is not a bzip2 file.
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [73.0 kB]
75% [67 Packages bzip2 0 B] [Waiting for headers] [34 Sources 2,801 kB/4,6bzip2: (stdin) is not a bzip2 file.
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex [4,683 B]
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex [546 kB]
E: Unable to parse package file /var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index (1)

---

### Post by dino99 on 2012-10-26
if the index is borked, then delete it and redo  :P:P

---

