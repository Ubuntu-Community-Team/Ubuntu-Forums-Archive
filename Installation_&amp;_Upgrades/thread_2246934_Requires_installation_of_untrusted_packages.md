---
title: "Requires installation of untrusted packages"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by panthersonu on 2014-10-04
hi i have ubuntu 10.04 window installed on my laptop when i try to install something from ubuntu software centre i got this msg "Requires installation of untrusted packages" The action would require the installation of packages from not authenticated sources. Please fix my problem n tell me how to solve it. when i run ths code on terminal ([LEFT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update)  i got this result
[/FONT][/COLOR][/LEFT]
```
faiza@faiza-Inspiron-N4050:~$ sudo apt-get update
[sudo] password for faiza: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/) maverick/main Translation-en_US
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) maverick-dell Release.gpg                
Ign [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) maverick-dell/public Translation-en
Ign [http://dell.archive.canonical.com/updates/](http://dell.archive.canonical.com/updates/) maverick-dell/public Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg                     
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en           
Ign [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main Translation-en_US        
Ign [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu/) maverick/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://ppa.launchpad.net/tucan/unstable/ubuntu/](http://ppa.launchpad.net/tucan/unstable/ubuntu/) maverick/main Translation-en
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) maverick-dell Release                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://ppa.launchpad.net/tucan/unstable/ubuntu/](http://ppa.launchpad.net/tucan/unstable/ubuntu/) maverick/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) maverick-dell/public Sources             
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release                       
Hit [http://dell.archive.canonical.com](http://dell.archive.canonical.com) maverick-dell/public i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://ppa.launchpad.net/tucan/unstable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/tucan/unstable/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/tucan/unstable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/tucan/unstable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]


E: Some index files failed to download, they have been ignored, or old ones used instead.
faiza@faiza-Inspiron-N4050:~$ 
```
 

plz tell me how to solve it?
[LEFT][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][/LEFT]

---

### Post by sammiev on 2014-10-04
It's looking for updates that are no longer availble. 
10.04 is end of life.

---

### Post by Topsiho on 2014-10-04
sammiev is quite right. Best thing to do is download a newer version of Ubuntu, preferably Ubuntu 14.04.1, or a similar version of Lubunru, Xubuntu or other, if you don't like Unity (which is, however, great if you get used to it). And use that for the install. Lububuntu and Xubuntu are lighter, but equivalent versions of Ubuntu, and use lighter desktops than Unity.

Topsiho

---

