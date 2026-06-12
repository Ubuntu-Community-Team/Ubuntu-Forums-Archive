---
title: "apt-get update won't work cause of &quot;Hash Sum mismatch&quot;"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by Ajite on 2012-09-11
Hi,

Since yesterday afternoon I've got this problem. I have just installed a new ubuntu 12.04 (32 bits) on my old computer and I get the following error message when I try to do an "apt-get update".

```
[B]ajite@ajite-PC:/var/lib/apt$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease                                                           
Ign http://us.archive.ubuntu.com precise-updates InRelease                                                   
Ign http://us.archive.ubuntu.com precise-backports InRelease
Ign http://us.archive.ubuntu.com precise-security InRelease
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]
Ign http://archive.canonical.com precise InRelease        
Get:4 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.canonical.com precise Release.gpg  
Get:5 http://us.archive.ubuntu.com precise Release [49.6 kB]
Hit http://archive.canonical.com precise Release   
Get:6 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://archive.canonical.com precise/partner i386 Packages                    
Get:7 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]
Ign http://archive.canonical.com precise/partner TranslationIndex                
Get:8 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]
Hit http://archive.canonical.com precise/partner Translation-en
Get:9 http://us.archive.ubuntu.com precise-security Release [49.6 kB]                                    
Ign http://us.archive.ubuntu.com precise-backports Release                                                   
Get:10 http://us.archive.ubuntu.com precise/main Sources [934 kB]                                            
Ign http://archive.canonical.com precise/partner Translation-en_US               
Get:11 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]                                              
Get:12 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]                                               
Get:13 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]                                               
Get:14 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]                                           
Get:15 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]                                     
Get:16 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]                                     
Get:17 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]                                       
Get:18 http://us.archive.ubuntu.com precise-updates/main Sources [162 kB]                                             
98% [13 Sources bzip2 0 B] [18 Sources 64.5 kB/162 kB 40%]                                                 221 kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:19 http://us.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]                                      
Get:20 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                             
Get:21 http://us.archive.ubuntu.com precise/restricted i386 Packages [4,786 kB]                                       
Get:22 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]                                         
Get:23 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                         
Get:24 http://us.archive.ubuntu.com precise-updates/universe Sources [50.8 kB]                                        
Get:25 http://us.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]                                      
Get:26 http://us.archive.ubuntu.com precise-updates/main i386 Packages [386 kB]                                       
Get:27 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]                                
Get:28 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [129 kB]                                   
Get:29 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                   
Get:30 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                             
Get:31 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                             
Get:32 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                               
Get:33 http://us.archive.ubuntu.com precise-backports/main Sources [2,422 B]                                          
Get:34 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                       
Get:35 http://us.archive.ubuntu.com precise-backports/universe Sources [14.2 kB]                                      
Get:36 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]                                    
Get:37 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [129 kB]                                   
Get:38 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [4,786 kB]                               
Get:39 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]                                    
Get:40 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                 
Get:41 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [12.4 kB]                                
Get:42 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]                                
Get:43 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]                                    
Get:44 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]                              
Get:45 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                              
Get:46 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]                                
Get:47 http://us.archive.ubuntu.com precise-security/main Sources [42.8 kB]                                           
Get:48 http://us.archive.ubuntu.com precise-security/restricted Sources [1,950 B]                                     
Get:49 http://us.archive.ubuntu.com precise-security/universe Sources [13.5 kB]                                       
Get:50 http://us.archive.ubuntu.com precise-security/multiverse Sources [1,386 B]                                     
Get:51 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [12.4 kB]                                
Get:52 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [3,968 B]                               
Get:53 http://us.archive.ubuntu.com precise-security/universe i386 Packages [44.0 kB]                                 
Get:54 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]                               
Get:55 http://us.archive.ubuntu.com precise-security/main TranslationIndex [73 B]                                     
Get:56 http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]                               
Get:57 http://us.archive.ubuntu.com precise-security/restricted TranslationIndex [71 B]                               
Get:58 http://us.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]                                 
Get:59 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]                                              
Get:60 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                       
Get:61 http://us.archive.ubuntu.com precise-security/main i386 Packages [133 kB]                                      
Get:62 http://us.archive.ubuntu.com precise-updates/main Translation-en [187 kB]                                      
Get:63 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [5,414 B]                               
Get:64 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [1,484 B]                               
Get:65 http://us.archive.ubuntu.com precise-updates/universe Translation-en [77.1 kB]                                 
Get:66 http://us.archive.ubuntu.com precise-backports/main Translation-en [1,244 B]                                   
Get:67 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [422 B]                               
Get:68 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                
Get:69 http://us.archive.ubuntu.com precise/restricted Translation-en [726 kB]                                        
Get:70 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                        
Get:71 http://us.archive.ubuntu.com precise-backports/universe Translation-en [9,070 B]                               
Get:72 http://us.archive.ubuntu.com precise-security/main Translation-en [76.5 kB]                                    
Get:73 http://us.archive.ubuntu.com precise-security/multiverse Translation-en [995 B]                                
Get:74 http://us.archive.ubuntu.com precise-security/restricted Translation-en [978 B]                                
Get:75 http://us.archive.ubuntu.com precise-security/universe Translation-en [27.2 kB]                                
Fetched 33.2 MB in 1min 5s (505 kB/s)                                                                                 
W: GPG error: http://us.archive.ubuntu.com precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/B]
```
After a deeper investigation I found out that the "apt-get update" won't  work with software source server using the HTTP protocol.  I have got  no problem with server using the FTP protocol.

I am in living in Shanghai and I don't use any proxy or VPN.

I have already  tried the following solutions:

**Solution 1:**

```

sudo apt-get clean
sudo apt-get update

```**Solution 2:**

```

cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

```**Solution 3**

Restore the trusted software providers default keys


I have seen that many people encountered similar problem but none of the solution that worked for them worked for me.

Thank you for your help.

---

### Post by plucky on 2012-09-12
Try changing your **Download Server**.

There has to be one closer to Shanghai than the US server.

Good luck

---

