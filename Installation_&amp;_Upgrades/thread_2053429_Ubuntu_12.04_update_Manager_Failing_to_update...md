---
title: "Ubuntu 12.04 update Manager Failing to update.."
date: 2012-09-05
forum: Installation &amp; Upgrades
---

### Post by vicky3p on 2012-09-05
Guys i'm new to linux n have been using 12.04 for last two months without any problems...but suddenly its not updating..whenever i try to open update manager it gives this error...

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.' error...

Even in terminal i tried to update but the same thing....i even tried to install synaptic but got this error instead..

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

Thanks in Advance for your help.....

---

### Post by cortman on 2012-09-05
> **vicky3p said:**
> Guys i'm new to linux n have been using 12.04 for last two months without any problems...but suddenly its not updating..whenever i try to open update manager it gives this error...

.

Even in terminal i tried to update but the same thing....i even tried to install synaptic but got this error instead..



Thanks in Advance for your help.....

Hi, run

```
sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-i386_Packages
sudo apt-get update
```

You apparently just have a bad package list. This will remove the old one and download a new one.

---

### Post by vicky3p on 2012-09-05
Ok tried that n got this...

> vikk@vikk:~$ sudo rm /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner _binary-i386_Packages
[sudo] password for vikk: 
rm: cannot remove `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner': No such file or directory
rm: cannot remove `_binary-i386_Packages': No such file or directory

n for sudo apt-get update i get this....

> vikk@vikk:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise InRelease                           
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates InRelease                   
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports InRelease                 
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security InRelease                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:1 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise Release.gpg [198 B]               
Get:2 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates Release.gpg [198 B]       
Get:3 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports Release.gpg [198 B]     
Get:4 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security Release.gpg [198 B]      
Get:5 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise Release [49.6 kB]                 
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:6 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates Release [49.6 kB]         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:7 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports Release [49.6 kB]       
Get:8 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:9 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security Release [49.6 kB]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:10 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main Sources [934 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources/DiffIndex             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:11 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted Sources [5,470 B]     
Get:12 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe Sources [5,019 kB]      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:13 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse Sources [155 kB]      
Get:14 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main i386 Packages [1,274 kB]    
Get:15 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted i386 Packages [8,431 B]
Get:16 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe i386 Packages [4,796 kB]
Get:17 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse i386 Packages [121 kB]
Get:18 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main TranslationIndex [3,706 B]  
Get:19 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse TranslationIndex [2,676 B]
Get:20 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted TranslationIndex [2,596 B]
Get:21 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe TranslationIndex [2,922 B]
Get:22 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main Sources [159 kB]    
Get:23 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted Sources [3,285 B]
Get:24 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe Sources [50.1 kB]
Get:25 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse Sources [4,241 B]
Get:26 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main i386 Packages [381 kB]
Get:27 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted i386 Packages [6,732 B]
Get:28 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe i386 Packages [127 kB]
Get:29 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse i386 Packages [9,672 B]
Get:30 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main TranslationIndex [3,564 B]
Get:31 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:32 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:33 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe TranslationIndex [2,850 B]
Get:34 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/main Sources [2,422 B] 
Get:35 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/restricted Sources [14 B]
Get:36 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/universe Sources [13.5 kB]
Get:37 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/multiverse Sources [1,383 B]
Get:38 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/main i386 Packages [1,941 B]
Get:39 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/restricted i386 Packages [14 B]
Get:40 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/universe i386 Packages [12.0 kB]
Get:41 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/multiverse i386 Packages [999 B]
Get:42 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/main TranslationIndex [72 B]
Get:43 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/multiverse TranslationIndex [71 B]
Get:44 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/restricted TranslationIndex [70 B]
Get:45 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/universe TranslationIndex [72 B]
Get:46 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main Sources [41.4 kB]  
Get:47 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted Sources [1,950 B]
Get:48 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe Sources [12.2 kB]
Get:49 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse Sources [1,386 B]
Get:50 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main i386 Packages [163 kB]
Get:51 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted i386 Packages [3,968 B]
Get:52 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe i386 Packages [41.6 kB]
Get:53 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse i386 Packages [2,369 B]
Get:54 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main TranslationIndex [73 B]
Get:55 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse TranslationIndex [71 B]
Get:56 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted TranslationIndex [71 B]
Get:57 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe TranslationIndex [73 B]
Get:58 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/main Translation-en [726 kB]     
Get:59 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/multiverse Translation-en [93.4 kB]
Get:60 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/restricted Translation-en [2,395 B]
Get:61 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise/universe Translation-en [3,341 kB]
Get:62 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/main Translation-en [184 kB]
Get:63 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/multiverse Translation-en [5,414 B]
Get:64 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/restricted Translation-en [1,484 B]
Get:65 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-updates/universe Translation-en [75.6 kB]
Get:66 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/main Translation-en [1,244 B]
Get:67 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/multiverse Translation-en [422 B]
Get:68 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/restricted Translation-en [14 B]
Get:69 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-backports/universe Translation-en [8,807 B]
Get:70 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/main Translation-en [75.2 kB]
Get:71 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/multiverse Translation-en [995 B]
Get:72 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/restricted Translation-en [978 B]
Get:73 [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) precise-security/universe Translation-en [25.7 kB]
Fetched 18.1 MB in 2min 30s (121 kB/s)                                         
Reading package lists... Error!
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


---

### Post by cortman on 2012-09-05
D'oh! Made a typo in my first command, sorry. To fix that and your GPG error, see [here]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").

---

### Post by vicky3p on 2012-09-05
Thanks mate that worked......

---

