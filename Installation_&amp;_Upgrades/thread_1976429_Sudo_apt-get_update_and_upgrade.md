---
title: "Sudo apt-get update and upgrade"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by NathanMartins on 2012-05-08
okay just installed the new 12.04 everything went great but when i ran sudo apt-get update  thsi is what i got

```
nathan@ubuntu:~$ sudo apt-get update
[sudo] password for nathan: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease           
Get:1 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise InRelease [2,326 B]
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise InRelease                             
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]      
Get:4 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates InRelease [2,334 B]      
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates InRelease                     
Get:5 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports InRelease [2,336 B]       
Ign [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports InRelease                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]   
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [2,245 B]                  
96% [7 Sources bzip2 0 B] [Connecting to br.archive.ubuntu.com (200.236.31.4)] bzip2: (stdin) is not a bzip2 file.
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [2,258 B]       
100% [8 Sources bzip2 0 B] [Waiting for headers] [Connecting to security.ubuntubzip2: (stdin) is not a bzip2 file.
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:9 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/main Sources/DiffIndex [2,346 B]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:10 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/restricted Sources/DiffIndex [2,353 B]
Get:11 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/universe Sources/DiffIndex [2,351 B]
Get:12 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/multiverse Sources/DiffIndex [2,353 B]
Get:13 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/main i386 Packages/DiffIndex [2,353 B]
Get:14 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex [2,359 B]
Get:15 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex [2,357 B]
Get:16 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex [2,359 B]
Get:17 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/main TranslationIndex [2,332 B]    
Get:18 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/multiverse TranslationIndex [2,338 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,264 B]
73% [19 Sources bzip2 0 B] [Connecting to br.archive.ubuntu.com (200.236.31.4)]bzip2: (stdin) is not a bzip2 file.
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [2,262 B]  
74% [20 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [2,264 B]
74% [21 Sources bzip2 0 B] [Connecting to br.archive.ubuntu.com (200.236.31.4)]bzip2: (stdin) is not a bzip2 file.
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [2,264 B]
75% [22 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitinbzip2: (stdin) is not a bzip2 file.
Get:23 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/restricted TranslationIndex [2,338 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [2,270 B]
74% [24 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitinbzip2: (stdin) is not a bzip2 file.
Get:25 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/universe TranslationIndex [2,336 B]
Get:26 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/main Sources/DiffIndex [2,355 B]
Get:27 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/restricted Sources [2,354 B]
71% [27 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [2,267 B]
72% [28 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitinbzip2: (stdin) is not a bzip2 file.
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,270 B]
72% [29 Packages bzip2 0 B] [Waiting for headers] [Connecting to security.ubuntbzip2: (stdin) is not a bzip2 file.
Get:30 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe Sources/DiffIndex [2,359 B]
Get:31 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/multiverse Sources/DiffIndex [2,361 B]
Get:32 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/main i386 Packages/DiffIndex [2,361 B]
Get:33 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/restricted i386 Packages/DiffIndex [2,367 B]
Get:34 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe i386 Packages/DiffIndex [2,365 B]
Get:35 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/multiverse i386 Packages/DiffIndex [2,367 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Get:36 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/main TranslationIndex [2,340 B]
Get:37 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,346 B]
Get:38 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,346 B]
Get:39 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,344 B]
Get:40 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/main Sources/DiffIndex [2,357 B]
Get:41 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex [2,362 B]
Get:42 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/universe Sources [2,354 B]
58% [42 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Get:43 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex [2,363 B]
Get:44 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex [2,363 B]
Get:45 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/restricted i386 Packages [2,362 B]
57% [45 Packages bzip2 0 B] [Connecting to br.archive.ubuntu.com] [Waiting for bzip2: (stdin) is not a bzip2 file.
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
  404  Not Found
Get:46 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US [2,243 B]       
Get:47 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en [2,240 B]          
Get:48 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/universe i386 Packages [2,360 B]
59% [48 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:49 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,362 B]
60% [49 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:50 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/main TranslationIndex [2,342 B]
Get:51 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/multiverse TranslationIndex [2,348 B]
Get:52 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/restricted TranslationIndex [2,348 B]
Get:53 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/universe TranslationIndex [2,346 B]
Get:54 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/main Sources [2,340 B]             
57% [54 Sources bzip2 0 B] [Waiting for headers]                  1,437 B/s 50sbzip2: (stdin) is not a bzip2 file.
Get:55 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/restricted Sources [2,346 B]       
57% [55 Sources bzip2 0 B] [Waiting for headers]                  1,437 B/s 50sbzip2: (stdin) is not a bzip2 file.
Get:56 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/universe Sources [2,344 B]         
58% [56 Sources bzip2 0 B] [Waiting for headers]                  1,437 B/s 50sbzip2: (stdin) is not a bzip2 file.
Get:57 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/multiverse Sources [2,346 B]       
59% [57 Sources bzip2 0 B] [Connecting to br.archive.ubuntu.com] [Connecting tobzip2: (stdin) is not a bzip2 file.
Get:58 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/main i386 Packages [2,346 B]       
59% [58 Packages bzip2 0 B] [Waiting for headers]                 2,241 B/s 32sbzip2: (stdin) is not a bzip2 file.
Get:59 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/restricted i386 Packages [2,352 B] 
60% [59 Packages bzip2 0 B] [Waiting for headers]                 2,241 B/s 32sbzip2: (stdin) is not a bzip2 file.
Get:60 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [2,263 B]
60% [60 Translation-en bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [2,269 B]
61% [61 Translation-en bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:62 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/universe i386 Packages [2,350 B] 
61% [62 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:63 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,268 B]
Get:64 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise/multiverse i386 Packages [2,352 B] 
bzip2: (stdin) is not a bzip2 file.
62% [64 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:65 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/main Sources [2,348 B]
62% [65 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
62% [27 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
Get:66 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe Sources [2,352 B] 
63% [66 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:67 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/multiverse Sources [2,354 B]
63% [67 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:68 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/main i386 Packages [2,354 B]
64% [68 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:69 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,360 B]
64% [69 Packages bzip2 0 B] [Connecting to br.archive.ubuntu.com] [Waiting for bzip2: (stdin) is not a bzip2 file.
Get:70 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [2,267 B]
65% [70 Translation-en bzip2 0 B] [Waiting for headers] [Connecting to securitybzip2: (stdin) is not a bzip2 file.
Get:71 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/universe i386 Packages [2,358 B]
65% [71 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:72 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,360 B]
65% [72 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:73 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/main Sources [2,350 B]
66% [73 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:74 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/restricted Sources [2,356 B]
66% [74 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
66% [42 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
Get:75 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/multiverse Sources [2,356 B]
67% [75 Sources bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:76 [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports/main i386 Packages [2,356 B]
67% [76 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
67% [45 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [48 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [49 Packages xz 0 B] [Connecting to br.archive.ubuntu.com] [Waiting for hea/usr/bin/xz: (stdin): File format not recognized
67% [54 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [55 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [56 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [57 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [58 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [59 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [62 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [64 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [65 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [27 Sources lzma 0 B] [Connecting to br.archive.ubuntu.com (200.236.31.4)] /usr/bin/lzma: (stdin): File format not recognized
67% [66 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [67 Sources xz 0 B] [Waiting for headers]                     2,703 B/s 26s/usr/bin/xz: (stdin): File format not recognized
67% [68 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [69 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [71 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [72 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [73 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [74 Sources xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [42 Sources lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [75 Sources xz 0 B] [Connecting to br.archive.ubuntu.com] [Waiting for head/usr/bin/xz: (stdin): File format not recognized
67% [76 Packages xz 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
67% [45 Packages lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [48 Packages lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [49 Packages lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [54 Sources lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [55 Sources lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [56 Sources lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [57 Sources lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [58 Packages lzma 0 B] [Waiting for headers] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [59 Packages lzma 0 B] [Connecting to br.archive.ubuntu.com] [Waiting for h/usr/bin/lzma: (stdin): File format not recognized
67% [62 Packages lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [64 Packages lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [65 Sources lzma 0 B] [Waiting for headers] [Connecting to security.ubuntu./usr/bin/lzma: (stdin): File format not recognized
67% [66 Sources lzma 0 B] [Waiting for headers] [Connecting to security.ubuntu./usr/bin/lzma: (stdin): File format not recognized
67% [67 Sources lzma 0 B] [Waiting for headers] [Connecting to security.ubuntu./usr/bin/lzma: (stdin): File format not recognized
67% [68 Packages lzma 0 B] [Connecting to security.ubuntu.com (91.189.92.151)]/usr/bin/lzma: (stdin): File format not recognized
67% [69 Packages lzma 0 B] [Connecting to security.ubuntu.com (91.189.92.151)]/usr/bin/lzma: (stdin): File format not recognized
67% [71 Packages lzma 0 B] [Waiting for headers] [Connecting to security.ubuntu/usr/bin/lzma: (stdin): File format not recognized
67% [72 Packages lzma 0 B] [Connecting to br.archive.ubuntu.com] [Connecting to/usr/bin/lzma: (stdin): File format not recognized
67% [73 Sources lzma 0 B]/usr/bin/lzma: (stdin): File format not recognized    
67% [74 Sources lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [75 Sources lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
67% [76 Packages lzma 0 B] [Waiting for headers]/usr/bin/lzma: (stdin): File format not recognized
Fetched 220 kB in 1min 8s (3,208 B/s)                          
W: GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise InRelease: File /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_InRelease doesn't start with a clearsigned message
W: GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-updates InRelease: File /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_InRelease doesn't start with a clearsigned message
W: GPG error: [http://br.archive.ubuntu.com](http://br.archive.ubuntu.com) precise-backports InRelease: File /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_InRelease doesn't start with a clearsigned message
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources  Encountered a section with no Package: header

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index

W: Failed to fetch [http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Index](http://br.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fUS  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/br.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.
nathan@ubuntu:~$
``` 
Any clue what might cause this ?????
Also this 

nathan@ubuntu:~$ sudo apt-get upgrade
[sudo] password for nathan: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/br.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
nathan@ubuntu:~$ 

sooo what is the problem ????

---

### Post by mörgæs on 2012-05-09
[http://ubuntuforums.org/showthread.php?t=1753045](http://ubuntuforums.org/showthread.php?t=1753045)

---

### Post by mungatsuma on 2012-08-19
Try changing the download server. It worked for me. Then update with code
```
sudo apt-get update
```

---

### Post by harishnair on 2012-08-26
Just uncheck "Important Security updates" from Software Sources settings and run 

sudo apt-get update

Then again check it back to get security updates and you will see the error wont be there.

It worked for me.

---

