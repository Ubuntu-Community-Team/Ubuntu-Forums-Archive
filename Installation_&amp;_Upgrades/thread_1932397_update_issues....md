---
title: "update issues..."
date: 2012-02-27
forum: Installation &amp; Upgrades
---

### Post by toastydust on 2012-02-27
ok so im running ubuntu 11.10 and when i run "sudo apt-get update" i get this message:     

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EA8F35793D8809A
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.


What do i do?

---

### Post by cortman on 2012-02-27
Hi,

Your GPG error can probably be fixed by the solutions in this [blog post]("http://cortman.wordpress.com/2012/02/27/how-to-fix-gpg-errors-in-ubuntu/").
The cdrom repositories can probably be safely deleted, unless you have a complete set of software CDs and are installing from them. Do this by editing your sources.list file:

```
gksu gedit /etc/apt/sources.list
```

Find the lines that refer to cdrom:, delete them and save. Then run

```
sudo apt-get update
```

Good luck!

---

### Post by raja.genupula on 2012-02-27
> **toastydust said:**
> ok so im running ubuntu 11.10 and when i run "sudo apt-get update" i get this message:     

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EA8F35793D8809A
W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.


What do i do?




open update manager -> settings -> in the first tab uncheck the CD-ROM check box .

 &
 open your terminal and type this

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

and let us know what you got .
All the best .

---

### Post by toastydust on 2012-03-13
ok so i did what was suggested about unchecking the cd rom box and thoroughly kicked myself for not looking there before then i did this:

dust@dust-GT5228:~$ sudo rm -rf /var/lib/apt/lists/*
dust@dust-GT5228:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:4 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg [316 B]                     
Get:9 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]                     
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                      
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [40.8 kB]                  
Ign [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2 InRelease                                    
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,742 B]                      
Get:13 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources [4,055 B]            
Get:14 [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages [7,282 B]      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release [9,737 B]                      
Get:16 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [1,662 B]                 
Get:17 [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2 Release.gpg [189 B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]          
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [2,477 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:20 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [839 B]                   
Get:21 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [2,830 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:22 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources [712 B]                   
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages [2,758 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:25 [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2 Release [79.9 kB]                         
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [34.5 kB]      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]   
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [12.2 kB]  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,654 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [90.4 kB]
Get:31 [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2/main i386 Packages [8,269 B]              
Ign [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2/main TranslationIndex                        
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [30.4 kB]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,362 B]
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [50.7 kB]
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en [1,494 B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [21.4 kB]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]       
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]        
Ign [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2/main Translation-en_US                       
Ign [http://linux.avasys.jp](http://linux.avasys.jp) lsb3.2/main Translation-en                          
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]        
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]    
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [130 kB]      
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [46.9 kB] 
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,648 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [299 kB]
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:60 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [103 kB]
Get:61 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,359 B]
Get:62 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:63 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:64 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:65 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:66 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en [701 kB]       
Get:67 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]
Get:68 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]
Get:69 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB] 
Get:70 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [141 kB]
Get:71 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3,524 B]
Get:72 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en [508 B]
Get:73 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [61.8 kB]
Fetched 16.8 MB in 1min 41s (166 kB/s)                                         
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EA8F35793D8809A
dust@dust-GT5228:~$ 


still got that error at the end but no more red triangle in my status bar so yay for that!!
this whole thing started because i was trying to get java to work on this machine...was working fine until i upgraded from 11.04 to 11.10...i still dont know what to do to make it work...tried JDK and JRE and any other acronym you can think of if anyone has any advice as far as that goes please let me know.
[RIGHT]Thanks...ToAsT
[/RIGHT]

---

### Post by oniea on 2012-04-30
c/p fixed it for me    

sudo gpg --export --armor 2EA8F35793D8809A | sudo apt-key add -

took the referance from     

[http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/](http://amazing-development.com/archives/2006/02/24/fixing-gpg-errors-with-apt-get-for-dummies-like-me/)

 have a good day all.

- 36minutes later same error one diffrent pc. 
Solution is c/p your key instead of the 2EA8 ect.

sudo gpg --export --armor "your key here" | sudo apt-key add -

---

