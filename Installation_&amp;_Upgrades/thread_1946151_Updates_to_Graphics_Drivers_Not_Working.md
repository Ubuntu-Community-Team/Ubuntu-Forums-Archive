---
title: "Updates to Graphics Drivers Not Working"
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by njrob on 2012-03-24
Hi, I'm trying to get OpenGL 3d graphics support for my Dell Latitude D810, which has a Graphics card that is no longer supported by "conventional" drivers.  That said, it is crucial for me to get drivers that DO work, and the ones I've found are not updating properly.

as far as I can tell, the launchpad ppa either isn't added to my software sources, or it isn't there at all.  I ran the following in a terminal.  Please let me know if I'm posting in the right place or if I can get any help here.  In any event, Thank you for your assistance.

neal@ubuntu:~$ sudo apt-get update
[sudo] password for neal: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric InRelease              
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release.gpg
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric Release
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) oneiric/main Translation-en
W: Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net///ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net///ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/xorg-edgers/drivers-only/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
neal@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xserver-xorg-video-openchrome
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
neal@ubuntu:~$

---

### Post by Mark Phelps on 2012-03-24
I don't know what you mean by "conventional" drivers.  

There are "open source" drivers and there are "restricted" drivers. These latter drivers provide 3D acceleration.

For that chipset, there are no restricted drivers that will work with it and any Ubuntu version newer than 8.10.  The open-source drivers are installed by default, and those are the ones that actually work.

You will need to remove the other drivers you installed and replace them with the open source Radeon drivers.

---

### Post by Mark Phelps on 2012-03-24
xxx

---

### Post by njrob on 2012-03-24
I discovered during my struggles with driver issues that the open source drivers installed by default are current enough that they do not support my graphics card either; mine is SOOOOO old, that I have found multiple sources claiming that the current Windows ATI and linux equivalents do not support my card, but that experimental open source drivers are in the making, if a little buggy for the interim.  I am attempting to use these experimental drivers because they are being made specifically for people trying to find drivers for outdated graphics cards like mine.

Sorry, I wasn't entirely clear before; does this explanation help you help me?  Don't get me wrong, I'm very grateful for your advice!  Thank you!

---

### Post by njrob on 2012-03-24
Oh, and by "conventional" I meant the newer open source drivers installed by default in the latest Ubuntu distribution.

---

### Post by Mark Phelps on 2012-03-26
The open-source drivers are constantly undergoing revision, so even if they did not work well with a previous Ubuntu version, that's no indication if they will still work poorly with a newer Ubuntu version.

To see what make and model video card you have, open a terminal and enter "lspci" (without the quotes).  Look for the line containing "VGA" -- and post that information back here.

That will tell us if you have a card that will take the current AMD restricted drivers.

---

