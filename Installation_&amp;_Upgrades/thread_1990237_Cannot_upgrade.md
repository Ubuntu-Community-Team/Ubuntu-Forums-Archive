---
title: "Cannot upgrade"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Sorceress on 2012-05-29
error message says 

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]


so what do i do next

---

### Post by plucky on 2012-05-29
> **Sorceress said:**
> error message says 

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages](http://ca.archive.ubuntu.com/ubuntu/dists/karmic-backports/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.154 80]


so what do i do next


Karmic is no longer supported and the repositories have been closed.
What version of Ubuntu are you running?

If it is Karmic,you should upgrade.

Good Luck

---

### Post by Sorceress on 2012-05-29
11.04 

it is trying to get karmic when i upgrade to 11.10

didn't have this problem when i upgraded from 10.10 trying to get system updated to latest version as fox is telling me my VLC is out of date and only way to update that is to update the os

---

### Post by plucky on 2012-05-29
> **Sorceress said:**
> 11.04 

it is trying to get karmic when i upgrade to 11.10

didn't have this problem when i upgraded from 10.10 trying to get system updated to latest version as fox is telling me my VLC is out of date and only way to update that is to update the os

If you are running 11.04, it should be ok to upgrade to 11.10.

Post your sources.list as it might have entries that shouldn't be there.

Good Luck

---

### Post by garvinrick4 on 2012-05-29
How did you attempt to upgrade? That is wierd it is trying to upgrade to karmic backports. 

Post your  gedit /etc/apt/sources.list to this thread like previous thread asked.  Open terminal
and:
```
gedit /etc/apt/sources.list
```and copy and paste whole sources list to this thread.

For time being did you try to remove check by backports and open a terminal and: (Will be in Software Sources.) (click on Thumbnail below)
```
sudo apt-get update
```

---

### Post by Sorceress on 2012-05-29
source list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner

doing sudo apt-get update gets me this

Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports InRelease                    
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick InRelease                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports Release.gpg                  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg [198 B]                      
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release.gpg [198 B]              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports Release                      
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release.gpg [198 B]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release [39.8 kB]                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports/main TranslationIndex        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports/multiverse TranslationIndex  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports/restricted TranslationIndex  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-backports/universe TranslationIndex    
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates Release [39.8 kB]                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security Release [39.8 kB]               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main TranslationIndex                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources [862 kB]                    

last cd-rom used was 7.10 have updated from update manager since then 

plus i am running ubuntu classic on 11.04 as it's tell me my hardware is not compatible with unity

---

### Post by Sorceress on 2012-05-29
figure out what it was

---

