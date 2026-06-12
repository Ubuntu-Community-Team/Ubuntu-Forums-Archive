---
title: "Could not initialize package information"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by ahmed32990 on 2012-06-05
During updating ubuntu i get this problem, i have attached a screenshot of the error that pops up. whenever i try to open the software center it would open and then close by itself after a few seconds. please help.

Thanks in advance.

Edit: 
Also whenever i try
 sudo apt-get clean
 sudo apt-get update
 sudo apt-get upgrade
even when i use 
 sudo rm -vf /var/lib/apt/lists/*

this is what i get :```

Get:2 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates Release.gpg [198 B]
Get:3 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports Release.gpg [198 B]
Get:4 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security Release.gpg [198 B]
Get:5 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise Release [49.6 kB]
Get:6 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates Release [49.6 kB]              
Get:7 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports Release [49.6 kB]            
Get:8 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security Release [49.6 kB]             
Get:9 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main Sources [934 kB]                    
Get:10 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted Sources [5,470 B]            
Get:11 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe Sources [5,019 kB]             
Get:12 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse Sources [155 kB]             
Get:13 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main i386 Packages [1,274 kB]           
Get:14 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted i386 Packages [8,431 B]      
Get:15 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe i386 Packages [4,796 kB]       
Get:16 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse i386 Packages [121 kB]       
Get:17 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main TranslationIndex [3,706 B]         
Get:18 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse TranslationIndex [2,676 B]
Get:19 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted TranslationIndex [2,596 B]
Get:20 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe TranslationIndex [2,922 B]     
Get:21 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main Sources [97.8 kB]          
Get:22 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted Sources [1,379 B]    
Get:23 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe Sources [19.6 kB]      
Get:24 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse Sources [1,053 B]    
Get:25 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main i386 Packages [234 kB]     
Get:26 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted i386 Packages [2,439 B]
Get:27 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe i386 Packages [57.9 kB]
Get:28 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse i386 Packages [2,046 B]
Get:29 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main TranslationIndex [74 B]    
Get:30 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse TranslationIndex [71 B]
Get:31 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted TranslationIndex [71 B]
Get:32 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe TranslationIndex [73 B]
Get:33 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main Sources [700 B]          
Get:34 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted Sources [14 B]     
Get:35 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe Sources [6,109 B]    
Get:36 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse Sources [1,383 B]  
Get:37 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main i386 Packages [559 B]    
Get:38 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted i386 Packages [14 B]
Get:39 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe i386 Packages [5,227 B]
Get:40 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse i386 Packages [999 B]
Get:41 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main TranslationIndex [71 B]  
Get:42 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse TranslationIndex [71 B]
Get:43 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted TranslationIndex [70 B]
Get:44 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe TranslationIndex [72 B]
Get:45 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main Sources [14.9 kB]         
Get:46 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted Sources [14 B]      
Get:47 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe Sources [4,935 B]     
Get:48 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse Sources [696 B]     
Get:49 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main i386 Packages [49.4 kB]   
Get:50 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted i386 Packages [14 B]
Get:51 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe i386 Packages [11.6 kB]
Get:52 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse i386 Packages [1,393 B]
Get:53 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main TranslationIndex [73 B]   
Get:54 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse TranslationIndex [71 B]
Get:55 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted TranslationIndex [70 B]
Get:56 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe TranslationIndex [72 B]
Get:57 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main Translation-en [726 kB]            
Get:58 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse Translation-en [93.4 kB]     
Get:59 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted Translation-en [2,395 B]     
Get:60 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe Translation-en [3,341 kB]      
Get:61 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main Translation-en [109 kB]    
Get:62 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse Translation-en [912 B]
Get:63 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted Translation-en [798 B]
Get:64 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe Translation-en [34.4 kB]
Get:65 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main Translation-en [308 B]   
Get:66 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse Translation-en [422 B]
Get:67 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted Translation-en [14 B]
Get:68 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe Translation-en [3,509 B]
Get:69 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main Translation-en [24.9 kB]  
Get:70 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse Translation-en [587 B]
Get:71 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted Translation-en [14 B]
Get:72 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe Translation-en [8,506 B]
Fetched 17.4 MB in 6min 8s (47.2 kB/s)                                         
Reading package lists... Done
ahmed@ahmed-Vostro-1500:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 thunderbird-globalmenu : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed
 thunderbird-gnome-support : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed
E: Unmet dependencies. Try using -f.
ahmed@ahmed-Vostro-1500:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ahmed@ahmed-Vostro-1500:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_source_Sources'
ahmed@ahmed-Vostro-1500:~$ sudo apt-get clean
ahmed@ahmed-Vostro-1500:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                       
Ign [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise InRelease      
Ign [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates InRelease
Ign [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports InRelease
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [476 B]               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [555 B]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                
Ign [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security InRelease
Get:5 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise Release.gpg [198 B]
Get:6 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates Release.gpg [198 B]
Get:7 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports Release.gpg [198 B]       
Get:8 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security Release.gpg [198 B]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Get:9 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise Release [49.6 kB]
Get:10 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates Release [49.6 kB]
Get:11 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports Release [49.6 kB]            
Get:12 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security Release [49.6 kB]              
Get:13 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main Sources [934 kB]                   
Get:14 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted Sources [5,470 B]            
Get:15 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe Sources [5,019 kB]             
Get:16 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse Sources [155 kB]             
Get:17 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main i386 Packages [1,274 kB]           
Get:18 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted i386 Packages [8,431 B]      
Get:19 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe i386 Packages [4,796 kB]       
Get:20 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse i386 Packages [121 kB]       
Get:21 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main TranslationIndex [3,706 B]         
Get:22 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse TranslationIndex [2,676 B]
Get:23 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted TranslationIndex [2,596 B]
Get:24 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe TranslationIndex [2,922 B]  
Get:25 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main Sources [97.8 kB]       
Get:26 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted Sources [1,379 B]    
Get:27 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe Sources [19.6 kB]      
Get:28 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse Sources [1,053 B]    
Get:29 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main i386 Packages [234 kB]     
Get:30 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted i386 Packages [2,439 B]
Get:31 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe i386 Packages [57.9 kB]
Get:32 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse i386 Packages [2,046 B]
Get:33 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main TranslationIndex [74 B]    
Get:34 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse TranslationIndex [71 B]
Get:35 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted TranslationIndex [71 B]
Get:36 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe TranslationIndex [73 B]
Get:37 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main Sources [700 B]          
Get:38 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted Sources [14 B]     
Get:39 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe Sources [6,109 B]    
Get:40 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse Sources [1,383 B]  
Get:41 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main i386 Packages [559 B]    
Get:42 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted i386 Packages [14 B]
Get:43 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe i386 Packages [5,227 B]
Get:44 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse i386 Packages [999 B]
Get:45 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main TranslationIndex [71 B]  
Get:46 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse TranslationIndex [71 B]
Get:47 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted TranslationIndex [70 B]
Get:48 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe TranslationIndex [72 B]
Get:49 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main Sources [14.9 kB]         
Get:50 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted Sources [14 B]      
Get:51 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe Sources [4,935 B]     
Get:52 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse Sources [696 B]     
Get:53 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main i386 Packages [49.4 kB]   
Get:54 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted i386 Packages [14 B]
Get:55 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe i386 Packages [11.6 kB]
Get:56 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse i386 Packages [1,393 B]
Get:57 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main TranslationIndex [73 B]   
Get:58 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse TranslationIndex [71 B]
Get:59 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted TranslationIndex [70 B]
Get:60 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe TranslationIndex [72 B]
Get:61 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/main Translation-en [726 kB]            
Get:62 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/multiverse Translation-en [93.4 kB]     
Get:63 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/restricted Translation-en [2,395 B]     
Get:64 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise/universe Translation-en [3,341 kB]      
Get:65 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/main Translation-en [109 kB]    
Get:66 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/multiverse Translation-en [912 B]
Get:67 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/restricted Translation-en [798 B]
Get:68 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-updates/universe Translation-en [34.4 kB]
Get:69 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/main Translation-en [308 B]   
Get:70 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/multiverse Translation-en [422 B]
Get:71 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/restricted Translation-en [14 B]
Get:72 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-backports/universe Translation-en [3,509 B]
Get:73 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/main Translation-en [24.9 kB]  
Get:74 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/multiverse Translation-en [587 B]
Get:75 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/restricted Translation-en [14 B]
Get:76 [http://ubuntu.mirror.tn](http://ubuntu.mirror.tn) precise-security/universe Translation-en [8,506 B]
Fetched 17.4 MB in 6min 2s (48.0 kB/s)                                         
Reading package lists... Done
ahmed@ahmed-Vostro-1500:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 thunderbird-globalmenu : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed
 thunderbird-gnome-support : Depends: thunderbird (= 12.0.1+build1-0ubuntu0.12.04.1) but 11.0.1+build1-0ubuntu2 is installed
E: Unmet dependencies. Try using -f.
ahmed@ahmed-Vostro-1500:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ahmed@ahmed-Vostro-1500:~$ sudo rm -vf /var/lib/apt/lists/*
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-security_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_Release'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/ubuntu.mirror.tn_dists_precise-updates_universe_source_Sources'
```

---

