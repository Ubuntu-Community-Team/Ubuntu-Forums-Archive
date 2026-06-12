---
title: "unable to update"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2013-04-26
Hi There, when I try to update through the terminal I get the message below. If I use the update icon on my menu bar...it simply does not start

what to do?


Fetched 19.8 MB in 25s (768 kB/s)                                              
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by dino99 on 2013-04-26
Its time to use alive distro  :P

[http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/](http://fridge.ubuntu.com/2012/04/10/ubuntu-10-10-maverick-meerkat-end-of-life-reached-on-april-10-2012/)

---

### Post by plucky on 2013-04-26
> **abelito8 said:**
> Hi There, when I try to update through the terminal I get the message below. If I use the update icon on my menu bar...it simply does not start

what to do?


Fetched 19.8 MB in 25s (768 kB/s)                                              
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.176 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

Are you running 10.10 Maverick?

If not, open Software Sources and disable any source that says **Maverick** in it and then reload from a terminal and see if you get the same error.

If you are running Maverick,I believe it has reached EOL a year ago and the repositories are closed.

Good Luck

---

### Post by abelito8 on 2013-04-26
Thanks, the problem is that I am using 12.04 LTS, not Maverick

I have disabled all Maverick sources (I only had the medibuntu ones) but it's still not working....

---

### Post by plucky on 2013-04-26
> **abelito8 said:**
> Thanks, the problem is that I am using 12.04 LTS, not Maverick

I have disabled all Maverick sources (I only had the medibuntu ones) but it's still not working....

Is it the same problem?

Open a terminal and post output for ```
sudo apt-get update
```

---

### Post by abelito8 on 2013-04-26
> **plucky said:**
> Is it the same problem?

Open a terminal and post output for ```
sudo apt-get update
```

Here you have



Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                              
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B]          
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release.gpg [198 B]           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release.gpg                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:5 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg [489 B]                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports Release                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                                  
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main Sources/DiffIndex     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:7 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release [2,603 B]                       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe Sources/DiffIndex 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse Sources/DiffIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:10 [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages [1,148 B]           
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed Release [49.6 kB]            
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main Sources               
  404  Not Found [IP: 91.189.92.200 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted Sources         
  404  Not Found [IP: 91.189.92.200 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe Sources           
  404  Not Found [IP: 91.189.92.200 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex                     
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/multiverse Sources         
  404  Not Found [IP: 91.189.92.200 80]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex                
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [379 kB]         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en      
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [85.4 kB] 
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [6,562 B]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_GB 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [612 kB]
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en                       
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [197 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex        
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [24.3 kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [2,504 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex      
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [69.6 kB]       
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [24.0 kB]   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [1,389 B] 
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [259 kB]  
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [73.4 kB]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [2,368 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex       
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted i386 Packages [14 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main i386 Packages [57.5 kB] 
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse i386 Packages [1,733 B]
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe i386 Packages [15.4 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted TranslationIndex     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en_GB                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en_GB             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en_GB             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en_GB           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en_GB     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en_GB       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en_GB          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/main Translation-en             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/multiverse Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en_GB    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/restricted Translation-en       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en_GB      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-proposed/universe Translation-en         
Fetched 2,054 kB in 17s (118 kB/s)                                             
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources](http://gb.archive.ubuntu.com/ubuntu/dists/maverick-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
abelito@ubuntu:~$

---

### Post by plucky on 2013-04-26
> Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/main Sources
404 Not Found [IP: 91.189.92.200 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/restricted Sources
404 Not Found [IP: 91.189.92.200 80]
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) maverick-backports/universe Sources
404 Not Found [IP: 91.189.92.200 80]

It is still looking for maverick-backports so you haven't removed all of the maverick repositories.

Post output for ```
cat /etc/apt/sources.list
```

---

### Post by abelito8 on 2013-04-26
> **plucky said:**
> It is still looking for maverick-backports so you haven't removed all of the maverick repositories.

Post output for ```
cat /etc/apt/sources.list
```

here it goes



cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-proposed restricted main multiverse universe

---

### Post by plucky on 2013-04-26
> deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and delete the line ```
deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
``` 
Then run ```
sudo apt-get update
``` again.

Good Luck

---

### Post by abelito8 on 2013-04-26
Thank you! It worked, now I only have to look for the solved button...

---

