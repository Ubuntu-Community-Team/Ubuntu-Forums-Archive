---
title: "updates12.04LTS"
date: 2013-06-06
forum: Installation &amp; Upgrades
---

### Post by anish789 on 2013-06-06
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or open

I am unable to update the packages.

---

### Post by fantab on 2013-06-07
Welcome to the forum!

From the Terminal [ctrl+alt+T] run the following command and post the output of it here:

```
sudo apt-get update
```

---

### Post by anish789 on 2013-06-07
ubuntu9@ubuntu:~$ sudo apt-get update
[sudo] password for ubuntu9: 
Sorry, try again.
[sudo] password for ubuntu9: 
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]         
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release                              
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [79.1 kB]       
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [25.7 kB]  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe TranslationIndex             
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Sources [395 kB]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,380 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [285 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [75.3 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,179 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [301 kB] 
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Sources [90.5 kB] 
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main amd64 Packages [634 kB]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [77.8 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,375 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [137 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [47.6 kB]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe amd64 Packages [206 kB]
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main i386 Packages [649 kB]
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe i386 Packages [209 kB]
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]                                                                                            
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                                                                               
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                                                                         
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                                                                         
Get:43 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                                                                           
Get:44 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Sources [2,899 B]                                                                                                      
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                                                                                   
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Sources [30.5 kB]                                                                                                  
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Sources [4,385 B]                                                                                                
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main amd64 Packages [2,383 B]                                                                                               
Get:49 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                                                                                            
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe amd64 Packages [30.6 kB]                                                                                           
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [4,609 B]                                                                                         
Get:52 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main i386 Packages [2,376 B]                                                                                                
Get:53 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                                                                                             
Get:54 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe i386 Packages [30.7 kB]                                                                                            
Get:55 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse i386 Packages [4,594 B]                                                                                          
Get:56 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]                                                                                                
Get:57 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]                                                                                          
Get:58 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]                                                                                          
Get:59 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe TranslationIndex [73 B]                                                                                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Translation-en                                                                                                                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Translation-en                                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Translation-en                                                                                                                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Translation-en                                                                                                                  
Get:60 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/main Translation-en [289 kB]                                                                                                  
Get:61 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/multiverse Translation-en [7,834 B]                                                                                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/restricted Translation-en                                                                                                        
Get:62 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates/universe Translation-en [121 kB]                                                                                              
Get:63 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/main Translation-en [1,512 B]                                                                                               
Get:64 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/multiverse Translation-en [4,043 B]                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/restricted Translation-en                                                                                                      
Get:65 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports/universe Translation-en [22.8 kB]                                                                                           
Fetched 4,013 kB in 33s (119 kB/s)                                                                                                                                                
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
ubuntu9@ubuntu:~$

---

### Post by sandyd on 2013-06-07
Try the below

**Remove the MergeLists**
```
sudo rm /var/lib/apt/lists/* -vf
```
**Re-Download the MergeLists**
```
sudo apt-get update
```

Please type the first command carefully - a space between the slashes will cause other files to be deleted!

---

