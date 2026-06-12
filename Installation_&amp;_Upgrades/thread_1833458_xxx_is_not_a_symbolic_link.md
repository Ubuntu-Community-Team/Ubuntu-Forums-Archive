---
title: "xxx is not a symbolic link"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-08-26
Since my last upgrade I find each time I want to install something at the end:

ldconfig deferred processing now taking place
/sbin/ldconfig.real: /usr/lib/libppsvodres.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsvodnet.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppssg.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsfds.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsapi.so.0 is not a symbolic link

/sbin/ldconfig.real: /usr/lib/libppsbase.so.0 is not a symbolic link


How can I get rid of that?

---

### Post by jerrrys on 2011-08-26
these lib files do not exist on my box.  so i googled it and the hits i get look like this:

[http://www.linuxsir.org/bbs/showthread.php?t=358005](http://www.linuxsir.org/bbs/showthread.php?t=358005)

looks like your dealing with some sort of local problem.  good luck

---

### Post by ELMIT on 2011-10-31
Does anybody have an idea how to solve that?

---

### Post by raja.genupula on 2011-10-31
could you please provide me the output of 
```
sudo apt-get update
```

Thank you man.

---

### Post by ELMIT on 2011-11-09
$ sudo apt-get update
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric InRelease
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security InRelease                    
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Get:2 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Get:3 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security Release.gpg [198 B]        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric Release                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Get:4 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:5 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates Release [32.4 kB]           
Get:6 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security Release [28.2 kB]          
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/universe Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/multiverse Sources                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/universe amd64 Packages     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en             
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:7 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/main Sources [68.5 kB]      
Get:8 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/restricted Sources [1,345 B]
Get:9 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/main amd64 Packages [129 kB]
Get:10 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages [2,882 B]
Get:11 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/universe amd64 Packages [37.1 kB]
Get:12 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages [2,698 B]
Get:13 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/main i386 Packages [129 kB]
Get:14 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,878 B]
Get:15 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/universe i386 Packages [37.4 kB]
Get:16 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [2,703 B]
Get:17 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:18 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:19 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:20 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:21 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/main Sources [7,141 B]    
Get:22 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/restricted Sources [14 B] 
Get:23 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/universe Sources [929 B]  
Get:24 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/multiverse Sources [14 B] 
Get:25 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/main amd64 Packages [16.0 kB]
Get:26 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/restricted amd64 Packages [14 B]
Get:27 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/universe amd64 Packages [5,742 B]
Get:28 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/multiverse amd64 Packages [14 B]
Get:29 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/main i386 Packages [16.1 kB]
Get:30 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:31 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/universe i386 Packages [5,748 B]
Get:32 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/multiverse i386 Packages [14 B]
Get:33 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:34 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [70 B]
Get:35 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:36 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/universe TranslationIndex [72 B]
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:37 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-updates/universe Translation-en [23.3 kB]
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/main Translation-en          
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/multiverse Translation-en    
Hit [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/restricted Translation-en    
Get:38 [http://tw.archive.ubuntu.com](http://tw.archive.ubuntu.com) oneiric-security/universe Translation-en [4,855 B]
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
  Connection failed [IP: 64.233.183.136 80]
Get:39 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]
Get:40 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                           
Get:41 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,220 B]               
Get:42 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,213 B]                
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex                  
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:43 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [764 B]                 
Get:44 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [779 B]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 561 kB in 11min 26s (817 B/s)
W: Failed to fetch [http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg](http://dl.google.com/linux/talkplugin/deb/dists/stable/Release.gpg)  Connection failed [IP: 64.233.183.136 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

