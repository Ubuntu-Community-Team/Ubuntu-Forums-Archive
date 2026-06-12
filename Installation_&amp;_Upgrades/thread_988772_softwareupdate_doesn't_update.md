---
title: "softwareupdate doesn't update"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by DudeOverdosed on 2008-11-20
Hi. I've got ubuntu 8.04 and i've tried to update through the software update application but i seem to be getting a problem. what i type in```
sudo apt-get update
``` it starts compiling but it doesn't install anything. the messages that i get are 
```
 
luig@luig-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 http://download.virtualbox.org hardy Release.gpg [189B]                  
Ign http://download.virtualbox.org hardy/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                  
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_US                      
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US     
Get:2 http://download.virtualbox.org hardy Release [2090B]                     
Ign http://download.virtualbox.org hardy Release                               
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US      
Hit http://download.virtualbox.org hardy/non-free Packages                     
Ign http://ppa.launchpad.net gutsy Release.gpg                                 
Ign http://ppa.launchpad.net gutsy/main Translation-en_US                      
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US       
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Hit http://archive.canonical.com hardy Release                                 
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com hardy Release                       
Get:4 http://ppa.launchpad.net gutsy Release [27.6kB]                          
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://us.archive.ubuntu.com hardy-updates Release                         
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Get:5 http://repoubuntusoftware.info harty Release.gpg [1722B]                 
Ign http://repoubuntusoftware.info harty/all Translation-en_US                 
Hit http://us.archive.ubuntu.com hardy/main Packages                           
Hit http://us.archive.ubuntu.com hardy/restricted Packages                     
Hit http://us.archive.ubuntu.com hardy/main Sources                            
Hit http://archive.canonical.com hardy/partner Sources                         
Ign http://ppa.launchpad.net gutsy/main Packages                     
Hit http://security.ubuntu.com hardy-security/multiverse Packages    
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://us.archive.ubuntu.com hardy/restricted Sources            
Hit http://us.archive.ubuntu.com hardy/universe Packages             
Hit http://us.archive.ubuntu.com hardy/universe Sources              
Hit http://us.archive.ubuntu.com hardy/multiverse Packages           
Hit http://us.archive.ubuntu.com hardy/multiverse Sources            
Hit http://us.archive.ubuntu.com hardy-updates/main Packages         
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://us.archive.ubuntu.com hardy-updates/main Sources          
Hit http://ppa.launchpad.net hardy/main Packages                     
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://ppa.launchpad.net gutsy/main Packages
Ign http://repoubuntusoftware.info harty Release
Ign http://repoubuntusoftware.info harty/all Packages
Hit http://repoubuntusoftware.info harty/all Packages
Fetched 1914B in 2s (926B/s)
W: GPG error: http://download.virtualbox.org hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

and I'm stuck. anyone know the problem?

---

