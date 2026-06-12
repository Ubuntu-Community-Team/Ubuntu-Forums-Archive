---
title: "update Ububnto 12.04 error: Failed to fetch"
date: 2012-08-06
forum: Installation &amp; Upgrades
---

### Post by zarriz on 2012-08-06
I use "sudo apt-get update" command in terminal and update process not complete and following error :

```
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease                       
Ign http://archive.ubuntu.com precise-backports InRelease                      
Ign http://archive.ubuntu.com precise-security InRelease                       
Ign http://extras.ubuntu.com precise InRelease                                 
Get:1 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Get:3 http://archive.ubuntu.com precise-backports Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release                                   
Ign https://private-ppa.launchpad.net precise InRelease                        
Get:4 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Hit http://extras.ubuntu.com precise/main Sources                              
Get:5 http://archive.ubuntu.com precise Release [49.6 kB]                      
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign https://private-ppa.launchpad.net precise Release.gpg                      
Ign https://private-ppa.launchpad.net precise Release                          
Get:6 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Ign http://archive.canonical.com precise InRelease                             
Ign https://private-ppa.launchpad.net precise/main i386 Packages/DiffIndex    
Get:7 http://archive.ubuntu.com precise-backports Release [49.6 kB]            
Hit http://archive.canonical.com precise Release.gpg                        
Get:8 http://archive.ubuntu.com precise-security Release [49.6 kB]          
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit http://archive.canonical.com precise Release                               
Get:9 http://archive.ubuntu.com precise/main Sources [934 kB]                  
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex            
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Get:10 http://archive.ubuntu.com precise/restricted Sources [5,470 B]          
Get:11 http://archive.ubuntu.com precise/universe Sources [5,019 kB]           
Err https://private-ppa.launchpad.net precise/main i386 Packages               
  HTTP response code said error
Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en              
Get:12 http://archive.ubuntu.com precise/multiverse Sources [155 kB]           
Get:13 http://archive.ubuntu.com precise/main i386 Packages [1,274 kB]         
Get:14 http://archive.ubuntu.com precise/restricted i386 Packages [8,431 B]    
Get:15 http://archive.ubuntu.com precise/universe i386 Packages [4,796 kB]     
Get:16 http://archive.ubuntu.com precise/multiverse i386 Packages [121 kB]     
Get:17 http://archive.ubuntu.com precise/main TranslationIndex [3,706 B]       
Get:18 http://archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B] 
Get:19 http://archive.ubuntu.com precise/restricted TranslationIndex [2,596 B] 
Get:20 http://archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:21 http://archive.ubuntu.com precise-updates/main Sources [144 kB] 
Get:22 http://archive.ubuntu.com precise-updates/restricted Sources [2,073 B]  
Get:23 http://archive.ubuntu.com precise-updates/universe Sources [45.8 kB]    
Get:24 http://archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]  
Get:25 http://archive.ubuntu.com precise-updates/main i386 Packages [349 kB]   
Get:26 http://archive.ubuntu.com precise-updates/restricted i386 Packages [3,949 B]
Get:27 http://archive.ubuntu.com precise-updates/universe i386 Packages [117 kB]
Get:28 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [2,540 B]
Get:29 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:30 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:31 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:32 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:33 http://archive.ubuntu.com precise-backports/main Sources [2,422 B]      
Get:34 http://archive.ubuntu.com precise-backports/restricted Sources [14 B]   
Get:35 http://archive.ubuntu.com precise-backports/universe Sources [12.4 kB]  
Get:36 http://archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:37 http://archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:38 http://archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:39 http://archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]
Get:40 http://archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Get:41 http://archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:42 http://archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]
Get:43 http://archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:44 http://archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Get:45 http://archive.ubuntu.com precise-security/main Sources [34.0 kB]       
Get:46 http://archive.ubuntu.com precise-security/restricted Sources [14 B]    
Get:47 http://archive.ubuntu.com precise-security/universe Sources [10.2 kB]   
Get:48 http://archive.ubuntu.com precise-security/multiverse Sources [713 B]   
Get:49 http://archive.ubuntu.com precise-security/main i386 Packages [125 kB]  
Get:50 http://archive.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:51 http://archive.ubuntu.com precise-security/universe i386 Packages [33.2 kB]
Get:52 http://archive.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:53 http://archive.ubuntu.com precise-security/main TranslationIndex [73 B] 
Get:54 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:55 http://archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:56 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:57 http://archive.ubuntu.com precise/main Translation-en [726 kB]          
Get:58 http://archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]   
Get:59 http://archive.ubuntu.com precise/restricted Translation-en [2,395 B]   
Get:60 http://archive.ubuntu.com precise/universe Translation-en [3,341 kB]    
Get:61 http://archive.ubuntu.com precise-updates/main Translation-en [165 kB]  
Get:62 http://archive.ubuntu.com precise-updates/multiverse Translation-en [1,600 B]
Get:63 http://archive.ubuntu.com precise-updates/restricted Translation-en [1,083 B]
Get:64 http://archive.ubuntu.com precise-updates/universe Translation-en [70.5 kB]
Get:65 http://archive.ubuntu.com precise-backports/main Translation-en [1,244 B]
Get:66 http://archive.ubuntu.com precise-backports/multiverse Translation-en [422 B]
Get:67 http://archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:68 http://archive.ubuntu.com precise-backports/universe Translation-en [8,334 B]
Get:69 http://archive.ubuntu.com precise-security/main Translation-en [61.6 kB]
Get:70 http://archive.ubuntu.com precise-security/multiverse Translation-en [587 B]
Get:71 http://archive.ubuntu.com precise-security/restricted Translation-en [14 B]
Get:72 http://archive.ubuntu.com precise-security/universe Translation-en [21.5 kB]
Fetched 17.9 MB in 1min 31s (197 kB/s)                                         
W: Failed to fetch https://private-ppa.launchpad.net/commercial-ppa-uploaders/master-pdf-editor/ubuntu/dists/precise/main/binary-i386/Packages  HTTP response code said error

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

i think this problem is related to "Master pdf editor" that i remove completely  but it not solved

---

### Post by cortman on 2012-08-06
So you don't use Master PDF Editor any more?
In that case, you should remove the ppa from your sources.list-

```
gksu gedit /etc/apt/sources.list
```

Find the line(s) relating to the MPE ppa and delete them.

Or if there's nothing in sources.list, run

```
gksu nautilus
```

Navigate to /etc/apt/sources.list.d/ and delete pertinent files.
Good luck!

---

### Post by zarriz on 2012-08-06
Thank you very much
problem solved

---

