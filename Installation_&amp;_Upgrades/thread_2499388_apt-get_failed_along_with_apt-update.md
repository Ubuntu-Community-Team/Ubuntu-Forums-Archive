---
title: "apt-get failed along with apt-update"
date: 2024-07-25
forum: Installation &amp; Upgrades
---

### Post by sonalagrawal on 2024-07-25
```
sonala@3mn19-Lin:~$ sudo apt-get install gnupg curl
[sudo] password for sonala: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_focal-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.


```

```
sonala@3mn19-Lin:~$ sudo apt update
Hit:1 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal InRelease                                                                                                                        
Hit:2 [https://pkg.cloudflareclient.com](https://pkg.cloudflareclient.com) focal InRelease                                                                                                                                
Hit:3 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                                                                                                                         
Hit:4 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal InRelease                                                                 
Get:5 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates InRelease [128 kB]                                         
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                                                              
Hit:7 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                           
Ign:8 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5 InRelease              
Hit:9 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5 Release
Fetched 128 kB in 3s (46.5 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_focal-updates_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

I tried sudo rm -vf /var/lib/apt/lists/*and then again sudo apt-get update and now the results are:

```
sonala@3mn19-Lin:~$ sudo apt-get update
Get:1 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease [1,825 B]
Get:2 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal InRelease [265 kB]                                                                                                                    
Get:3 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal InRelease [57.7 kB]                                                                                                              
Get:4 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) focal/stable amd64 Packages [48.0 kB]                                                                                                  
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [128 kB]                                                                                                             
Get:6 [https://pkg.cloudflareclient.com](https://pkg.cloudflareclient.com) focal InRelease [2,567 B]                                                                                                     
Get:7 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable/main amd64 Packages [1,086 B]                                                                                                  
Ign:8 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5 InRelease                                                                                 
Get:9 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates InRelease [128 kB]                           
Get:10 [https://pkg.cloudflareclient.com](https://pkg.cloudflareclient.com) focal/main amd64 Packages [459 B]                                      
Get:11 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5 Release [1,477 B]                              
Get:12 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports InRelease [128 kB]              
Get:13 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main i386 Packages [718 kB]             
Get:14 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5 Release.gpg [874 B]   
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages [3,086 kB]    
Get:16 [https://www.scootersoftware.com/debian](https://www.scootersoftware.com/debian) bcompare5/non-free amd64 Packages [813 B]    
Get:17 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main amd64 Packages [970 kB]                      
Get:18 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main Translation-en [506 kB]               
Get:19 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main amd64 DEP-11 Metadata [494 kB]               
Get:20 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main DEP-11 48x48 Icons [98.4 kB]                         
Get:21 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main DEP-11 64x64 Icons [163 kB]                          
Get:22 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main DEP-11 64x64@2 Icons [15.8 kB]                       
Get:23 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/main amd64 c-n-f Metadata [29.5 kB]                     
Get:24 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/restricted amd64 Packages [22.0 kB]                       
Get:25 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/restricted i386 Packages [8,112 B]                    
Get:26 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/restricted Translation-en [6,212 B]           
Get:27 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/restricted amd64 c-n-f Metadata [392 B]               
Get:28 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe i386 Packages [4,642 kB]         
Get:29 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main i386 Packages [789 kB]
Get:30 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main Translation-en [459 kB]           
Get:31 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [65.3 kB]     
Get:32 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main DEP-11 48x48 Icons [24.2 kB]                     
Get:33 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main DEP-11 64x64 Icons [42.9 kB]                     
Get:34 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main DEP-11 64x64@2 Icons [29 B]                    
Get:35 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [14.0 kB]
Get:36 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted amd64 Packages [2,985 kB]
Get:37 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages [8,628 kB]                                                                                                   
Get:38 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted i386 Packages [38.1 kB]                                                                                            
Get:39 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted Translation-en [417 kB]                                                                                            
Get:40 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted amd64 DEP-11 Metadata [212 B]                                                                                      
Get:41 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted DEP-11 48x48 Icons [29 B]                                                                                          
Get:42 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted DEP-11 64x64 Icons [29 B]                                                                                          
Get:43 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted DEP-11 64x64@2 Icons [29 B]                                                                                        
Get:44 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted amd64 c-n-f Metadata [544 B]                                                                                       
Get:45 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe i386 Packages [674 kB]                                                                                               
Get:46 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 Packages [996 kB]                                                                                              
Get:47 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe Translation-en [211 kB]                                                                                              
Get:48 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [127 kB]                                                                                       
Get:49 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe DEP-11 48x48 Icons [61.1 kB]                                                                                         
Get:50 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe DEP-11 64x64 Icons [117 kB]                                                                                          
Get:51 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe DEP-11 64x64@2 Icons [29 B]                                                                                          
Get:52 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [20.9 kB]                                                                                       
Get:53 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse i386 Packages [7,204 B]                                                                                            
Get:54 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 Packages [24.8 kB]                                                                                           
Get:55 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse Translation-en [5,968 B]                                                                                           
Get:56 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [940 B]                                                                                      
Get:57 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse DEP-11 48x48 Icons [1,867 B]                                                                                       
Get:58 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse DEP-11 64x64 Icons [2,497 B]                                                                                       
Get:59 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse DEP-11 64x64@2 Icons [29 B]                                                                                        
Get:60 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 c-n-f Metadata [540 B]                                                                                       
Get:61 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe Translation-en [5,124 kB]                                                                                                   
Get:62 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe amd64 DEP-11 Metadata [3,603 kB]                                                                                            
Get:63 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe DEP-11 48x48 Icons [3,016 kB]                                                                                               
Get:64 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe DEP-11 64x64 Icons [7,794 kB]                                                                                               
Get:65 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe DEP-11 64x64@2 Icons [44.3 kB]                                                                                              
Get:66 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/universe amd64 c-n-f Metadata [265 kB]                                                                                               
Get:67 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse i386 Packages [74.7 kB]                                                                                                   
Get:68 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse amd64 Packages [144 kB]                                                                                                   
Get:69 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse Translation-en [104 kB]                                                                                                   
Get:70 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse amd64 DEP-11 Metadata [48.4 kB]                                                                                           
Get:71 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse DEP-11 48x48 Icons [23.1 kB]                                                                                              
Get:72 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse DEP-11 64x64 Icons [192 kB]                                                                                               
Get:73 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse DEP-11 64x64@2 Icons [214 B]                                                                                              
Get:74 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal/multiverse amd64 c-n-f Metadata [9,136 B]                                                                                            
Get:75 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [3,455 kB]                                                                                               
Get:76 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [1,009 kB]                                                                                                
Get:77 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main Translation-en [538 kB]                                                                                                 
Get:78 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [276 kB]                                                                                          
Get:79 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main DEP-11 48x48 Icons [63.9 kB]                                                                                            
Get:80 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main DEP-11 64x64 Icons [102 kB]                                                                                             
Get:81 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main DEP-11 64x64@2 Icons [29 B]                                                                                             
Get:82 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/main amd64 c-n-f Metadata [17.7 kB]                                                                                          
Get:83 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted i386 Packages [39.4 kB]                                                                                           
Get:84 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 Packages [3,104 kB]                                                                                         
Get:85 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted Translation-en [434 kB]                                                                                           
Get:86 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 DEP-11 Metadata [212 B]                                                                                     
Get:87 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted DEP-11 48x48 Icons [29 B]                                                                                         
Get:88 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted DEP-11 64x64 Icons [29 B]                                                                                         
Get:89 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted DEP-11 64x64@2 Icons [29 B]                                                                                       
Get:90 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 c-n-f Metadata [540 B]                                                                                      
Get:91 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [800 kB]                                                                                              
Get:92 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [1,215 kB]                                                                                           
Get:93 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe Translation-en [293 kB]                                                                                             
Get:94 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [444 kB]                                                                                      
Get:95 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 48x48 Icons [294 kB]                                                                                         
Get:96 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 64x64 Icons [516 kB]                                                                                         
Get:97 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 64x64@2 Icons [29 B]                                                                                         
Get:98 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 c-n-f Metadata [27.5 kB]                                                                                      
Get:99 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 Packages [27.1 kB]                                                                                          
Get:100 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse i386 Packages [8,440 B]                                                                                          
Get:101 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse Translation-en [7,936 B]                                                                                         
Get:102 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [940 B]                                                                                    
Get:103 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse DEP-11 48x48 Icons [1,867 B]                                                                                     
Get:104 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse DEP-11 64x64 Icons [2,497 B]                                                                                     
Get:105 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse DEP-11 64x64@2 Icons [29 B]                                                                                      
Get:106 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 c-n-f Metadata [616 B]                                                                                     
Get:107 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main i386 Packages [36.1 kB]                                                                                              
Get:108 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main amd64 Packages [45.7 kB]                                                                                             
Get:109 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main Translation-en [16.3 kB]                                                                                             
Get:110 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main amd64 DEP-11 Metadata [7,980 B]                                                                                      
Get:111 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main DEP-11 48x48 Icons [7,156 B]                                                                                         
Get:112 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main DEP-11 64x64 Icons [10.7 kB]                                                                                         
Get:113 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main DEP-11 64x64@2 Icons [29 B]                                                                                          
Get:114 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/main amd64 c-n-f Metadata [1,420 B]                                                                                       
Get:115 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/restricted amd64 DEP-11 Metadata [212 B]                                                                                  
Get:116 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/restricted DEP-11 48x48 Icons [29 B]                                                                                      
Get:117 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/restricted DEP-11 64x64 Icons [29 B]                                                                                      
Get:118 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/restricted DEP-11 64x64@2 Icons [29 B]                                                                                    
Get:119 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/restricted amd64 c-n-f Metadata [116 B]                                                                                   
Get:120 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe i386 Packages [13.8 kB]                                                                                          
Get:121 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 Packages [25.0 kB]                                                                                         
Get:122 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe Translation-en [16.3 kB]                                                                                         
Get:123 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [30.5 kB]                                                                                  
Get:124 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe DEP-11 48x48 Icons [13.3 kB]                                                                                     
Get:125 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe DEP-11 64x64 Icons [22.7 kB]                                                                                     
Get:126 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe DEP-11 64x64@2 Icons [29 B]                                                                                      
Get:127 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 c-n-f Metadata [880 B]                                                                                     
Get:128 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/multiverse amd64 DEP-11 Metadata [212 B]                                                                                  
Get:129 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/multiverse DEP-11 48x48 Icons [29 B]                                                                                      
Get:130 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/multiverse DEP-11 64x64 Icons [29 B]                                                                                      
Get:131 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/multiverse DEP-11 64x64@2 Icons [29 B]                                                                                    
Get:132 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) focal-backports/multiverse amd64 c-n-f Metadata [116 B]                                                                                   
Fetched 60.6 MB in 32s (1,909 kB/s)                                                                                                                                                   
Segmentation fault
Segmentation fault
Reading package lists... Error!
E: Problem executing scripts APT::Update::Post-Invoke-Success 'if /usr/bin/test -w /var/lib/command-not-found/ -a -e /usr/lib/cnf-update-db; then /usr/lib/cnf-update-db > /dev/null; fi'
E: Sub-process returned an error code
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_focal_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```

---

### Post by TheFu on 2024-07-25
You have the order wrong.
Once a day, run 
```
sudo apt update
```
This pulls down the current, available, package lists for each repo and PPA configured in the system.

Then you should 
```
sudo apt upgrade
```
to get the current versions of all the packages already installed.  I upgrade/patch only once a week, so my systems are stable most of the time.

Then you can install any new packages ...
```
sudo apt install gnupg curl
```
In theory, doing an upgrade isn't required, but there are times when a new version of an uninstalled package may need an updated version of a package you already have. The dependencies should force that and I've only seen incorrect dependencies happen a few times in nearly 3 decades.

If you don't know exactly what you are doing, don't go deleting files manually.  The package manager has commands for maintenance.
```
sudo apt autoremove
sudo apt autoclean
```

There is little need to use apt-get, unless you just want to type more characters.  apt is a nearly complete replacement for apt-get.  I suspect any options that apt doesn't handle will cause it to involve apt-get for us.

If    /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_focal-updates_main_i18n_Translation-en is corrupted, I'd take a look at the file and see it is similar to other files like it.  If it isn't, I'd work through why it may have become corrupted.  Typically, that would be due to failing hardware, so check your storage, check your network for any other corruption.  For the storage, I'd use SMART data.  Also, if the partition for /var/ is full or near full, then it is likely that a full disk is the issue.  Solve that.

---

