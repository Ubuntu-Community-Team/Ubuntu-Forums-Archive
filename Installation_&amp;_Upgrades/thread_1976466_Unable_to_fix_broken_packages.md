---
title: "Unable to fix broken packages"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by timg37 on 2012-05-08
So I was trying to install Pidgin through Synaptic earlier, but I got this error message:

Could not apply changes!
Fix broken packages first.

I went to Edit>Fix Broken Packages to try to fix the broken packages, but I got this error message:

E: Unable to correct problems, you have held broken packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

Any idea on how I could fix the broken packages and complete my quest to have a better messenger than Empathy?

---

### Post by mörgæs on 2012-05-09
Try to boot the computer and run

```
sudo apt-get update
sudo apt-get upgrade
```

and watch the messages. 

Close all windows which might open in the process.

---

### Post by timg37 on 2012-05-09
When I do sudo apt-get update I get this:

timothy@grahambo:~$ sudo apt-get update
[sudo] password for timothy: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [7,089 B]       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [3,653 B]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [32.9 kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [8,581 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,142 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [32.9 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [8,594 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps amd64 Packages               
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps i386 Packages                
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps TranslationIndex             
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]     
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB] 
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en_US            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) oneiric-getdeb/apps Translation-en               
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [25.0 kB]     
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [765 B] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [8,304 B] 
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [696 B] 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [68.3 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [757 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [21.9 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,142 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [69.6 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [770 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [22.1 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,393 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [700 B]     
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [14 B]  
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [14 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [559 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [14 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [14 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [559 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [14 B]
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [14 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Get:58 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                         
Get:59 [http://dl.google.com](http://dl.google.com) stable Release [1,351 B]
Get:60 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,258 B]
Get:61 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,250 B]                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Fetched 19.0 MB in 2min 8s (148 kB/s)                                          
W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/gnome3/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Nothing special for sudo apt-get upgrade:
timothy@grahambo:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpurple0 tomboy
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

And I still can't install Pidgin :(

---

### Post by mörgæs on 2012-05-09
You have made quite a few experiments on this computer including at least one upgrade. 

There is some cruft from 11.10 in the sources.list, and a number of PPA's are referred, but not all are accessible. 

As 12.04 is only a few weeks old there is not much point in enabling backports.

If you will try to troubleshoot, the first step is to edit sources.list and comment out everything you don't need.

If you want to build a new sources.list from scratch you can do it here:
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

---

