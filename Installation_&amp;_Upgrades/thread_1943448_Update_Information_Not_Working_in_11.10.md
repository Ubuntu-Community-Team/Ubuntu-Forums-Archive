---
title: "Update Information Not Working in 11.10"
date: 2012-03-19
forum: Installation &amp; Upgrades
---

### Post by CCitizen on 2012-03-19
I was going along fine then suddenly like yesterday it decided to start giving me errors. I'm not sure what happened so I left it alone for a few days figuring it might be the servers or something causing the problem... Anyways here's what I get when I go and do 'sudo apt-get update'...

```

Ign http://ppa.launchpad.net oneiric InRelease
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ca.archive.ubuntu.com oneiric InRelease                             
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://ca.archive.ubuntu.com oneiric Release.gpg                           
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://ca.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://ca.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ca.archive.ubuntu.com oneiric-updates Release                       
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ca.archive.ubuntu.com oneiric/main Sources                          
Hit http://ca.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://ca.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ca.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://ca.archive.ubuntu.com oneiric/main amd64 Packages                   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ca.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://ca.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://ca.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://ca.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://ca.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ca.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ca.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ca.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ca.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://ppa.launchpad.net oneiric/main Sources                    
Hit http://ppa.launchpad.net oneiric/main amd64 Packages             
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://ca.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com oneiric/restricted Translation-en   
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_CA   
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA
Ign http://extras.ubuntu.com oneiric/main Translation-en
Err http://ppa.launchpad.net oneiric/main Sources
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```To me it looks like Ubuntu is not getting any updates for Oneiric (11.10) and according ot my update manager it hasnt for 8 days now.

---

### Post by CCitizen on 2012-03-19
Heres a copy of my /etc/apt/sources.list since someone said it would help...

```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ca.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse


```

---

### Post by Frogs Hair on 2012-03-19
The last distribution I see listed for the PPA at the bottom of the first output is 10.10. See the dist list.  Is it still maintained ?  [http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/](http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/)

---

### Post by jerrrys on 2012-03-19
anything in /etc/apt/sources.list.d ?

---

### Post by CCitizen on 2012-03-20
Here's the contents of /etc/apt/sources.list.d/

```

total 116
-rw-r--r-- 1 root root 160 2012-03-18 12:38 alexmurray-indicator-sensors-oneiric.list
-rw-r--r-- 1 root root 160 2012-03-18 12:38 alexmurray-indicator-sensors-oneiric.list.save
-rw-r--r-- 1 root root  84 2012-03-18 12:38 dropbox.list
-rw-r--r-- 1 root root  47 2011-10-14 22:05 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  84 2012-03-18 12:38 dropbox.list.save
-rw-r--r-- 1 root root 156 2012-03-18 12:38 felix_lechner-linphone-ppa-oneiric.list
-rw-r--r-- 1 root root 156 2012-03-18 12:38 felix_lechner-linphone-ppa-oneiric.list.save
-rw-r--r-- 1 root root 142 2012-03-18 12:38 i2p-maintainers-i2p-oneiric.list
-rw-r--r-- 1 root root 142 2012-03-18 12:38 i2p-maintainers-i2p-oneiric.list.save
-rw-r--r-- 1 root root 118 2012-03-18 12:38 jfi-ppa-oneiric.list
-rw-r--r-- 1 root root 118 2012-03-18 12:38 jfi-ppa-oneiric.list.save
-rw-r--r-- 1 root root 310 2012-03-18 12:38 medibuntu.list
-rw-r--r-- 1 root root 274 2011-10-14 22:05 medibuntu.list.distUpgrade
-rw-r--r-- 1 root root 310 2012-03-18 12:38 medibuntu.list.save
-rw-r--r-- 1 root root  82 2012-03-18 12:38 natty-partner.list
-rw-r--r-- 1 root root  80 2011-10-14 22:05 natty-partner.list.distUpgrade
-rw-r--r-- 1 root root  82 2012-03-18 12:38 natty-partner.list.save
-rw-r--r-- 1 root root 449 2012-03-18 12:38 opera.list
-rw-r--r-- 1 root root 416 2011-10-14 22:05 opera.list.distUpgrade
-rw-r--r-- 1 root root 449 2012-03-18 12:38 opera.list.save
-rw-r--r-- 1 root root 172 2012-03-18 12:38 pirate.list
-rw-r--r-- 1 root root 170 2012-03-18 12:38 pirate.list.save
-rw-r--r-- 1 root root 124 2012-03-18 12:38 slicer-ppa-oneiric.list
-rw-r--r-- 1 root root 124 2012-03-18 12:38 slicer-ppa-oneiric.list.save
-rw-r--r-- 1 root root 253 2012-03-18 12:38 stebbins-handbrake-releases-maverick.list
-rw-r--r-- 1 root root 218 2011-10-14 22:05 stebbins-handbrake-releases-maverick.list.distUpgrade
-rw-r--r-- 1 root root 253 2012-03-18 12:38 stebbins-handbrake-releases-maverick.list.save
-rw-r--r-- 1 root root 158 2012-03-18 12:38 stebbins-handbrake-releases-oneiric.list
-rw-r--r-- 1 root root 158 2012-03-18 12:38 stebbins-handbrake-releases-oneiric.list.save

```

---

### Post by jerrrys on 2012-03-20
Have you tried changing servers just to be sure?  Maybe try Main Server.

Im running a fairly fresh copy of 12o4 and have nothing in my sources.list.d so I cannot verify if this is correct and have asked for verification.  So please wait to see if others reply to this thread. But...

I would first make a backup of sources.list.d:

sudo cp /etc/apt/sources.list.d /etc/apt/sources.list.d.backup

And then edit out the offending PPA's.  I would think that you could just comment (#) out, but I also see just removing the ".list" from the address may work just as well.

This is my best guess-work, hope it helps.

[http://askubuntu.com/questions/82825/do-files-at-etc-apt-sources-list-d-need-to-have-an-extension-list](http://askubuntu.com/questions/82825/do-files-at-etc-apt-sources-list-d-need-to-have-an-extension-list)

[http://blog.ubuntu-tweak.com/guide/how-to-fix-the-source-list-files](http://blog.ubuntu-tweak.com/guide/how-to-fix-the-source-list-files)

---

### Post by CCitizen on 2012-03-21
I did that but somehow I have a feeling I'm not getting any updates now... since this is the result of sudo apt-get update

```

Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ca.archive.ubuntu.com oneiric InRelease                             
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ca.archive.ubuntu.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ca.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://archive.canonical.com oneiric Release                     
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://ppa.launchpad.net oneiric Release.gpg
Hit http://ca.archive.ubuntu.com oneiric Release                               
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://ca.archive.ubuntu.com oneiric-updates Release                       
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Hit http://security.ubuntu.com oneiric-security/universe Sources               
Hit http://security.ubuntu.com oneiric-security/multiverse Sources             
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ca.archive.ubuntu.com oneiric/main Sources                          
Hit http://ca.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://ca.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ca.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages        
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com oneiric-security/main i386 Packages             
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages       
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://ca.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Hit http://ca.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://ca.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://ca.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://ca.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://ca.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ca.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com oneiric/restricted TranslationIndex           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://ca.archive.ubuntu.com oneiric-updates/main Sources                  
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Sources              
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Sources            
Hit http://ca.archive.ubuntu.com oneiric-updates/main amd64 Packages           
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://ca.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse i386 Packages      
Hit http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Hit http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Get:1 http://ca.archive.ubuntu.com oneiric/main Translation-en_CA [9,465 B]    
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://ca.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://ca.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en       
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA                    
Ign http://archive.canonical.com oneiric/partner Translation-en_CA   
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA
Ign http://ppa.launchpad.net oneiric/main Translation-en
Fetched 9,465 B in 2s (3,751 B/s)
Reading package lists... Done

```

I have no clue it looks like /slicer/ one is not working

[http://ppa.launchpad.net/slicer/ppa/ubuntu](http://ppa.launchpad.net/slicer/ppa/ubuntu) oneiric main
[http://ppa.launchpad.net/slicer/ppa/ubuntu](http://ppa.launchpad.net/slicer/ppa/ubuntu) oneiric main (source code)

are these lines the ones that are ensuring i get proper Ubuntu updates now?

[http://ppa.launchpad.net/jfl/ppa/ubuntu](http://ppa.launchpad.net/jfl/ppa/ubuntu) oneiric main
[http://ppa.launchpad.net/jfl/ppa/ubuntu](http://ppa.launchpad.net/jfl/ppa/ubuntu) oneiric main (source code)

---

### Post by matt_symes on 2012-03-21
Hi

Open a terminal and copy and paste this into it.

```
sudo rm /etc/apt/sources.list.d/*maverick* /etc/apt/sources.list.d/slicer-ppa-*
```

It will remove you maverick PPAs and the slicer PPA. There is no Oneiric PPA for Slicer ([http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/](http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/)).

Then 

```
sudo apt-get update
```

Post back any errors. If there are no errors then try update manager.

Kind regards

---

### Post by jerrrys on 2012-03-21
PPA's are packages/app's that are not officially supported by Ubuntu, but can be added thru launchpad.  In your case it looks like you upgraded to 11.10 without properly preparing your software sources and have a mix of sources that wont work together.

The slicer PPA was giving 404 errors.  Removing it has cleared the problem.  Your last printout did not show any errors and is trying to work, but looks like you still have a mess.  I see both 32 and 64 bit software sources.  AMD64 stand for 64bit and i386 stands for 32 bit sources.

And you still have things in "list.d" that should not be there.  Maverick and Natty sources should be remove.  You may of added medibuntu for A?V reasons, but should of been removed before you upgrade to 11.10.

We can continue to clean up software sources, but don't know what else is going to go wrong in the process.

I would instead suggest a fresh install of 11.10 and not try to patch this copy back together.

[http://en.wikipedia.org/wiki/Personal_Package_Archive](http://en.wikipedia.org/wiki/Personal_Package_Archive)

---

### Post by jerrrys on 2012-03-21
Hi Matt:  I did not see your post for some reason until I posted. weird

---

### Post by matt_symes on 2012-03-21
Hi

> **jerrrys said:**
> Hi Matt:  I did not see your post for some reason until I posted. weird

Hi jerrrys ):P

Don't worry. I've done the same myself :smile:

Kind regards

---

### Post by jerrrys on 2012-03-21
> **matt_symes said:**
> Hi



Hi jerrrys ):P

Don't worry. I've done the same myself :smile:

Kind regards

I let it set there too long before I replied.  Should of reloaded.  Thats what happen:D

Anyhow you seen my reply.  What do you think about reinstall?

---

### Post by matt_symes on 2012-03-21
Hi jerrys

> **jerrrys said:**
> Anyhow you seen my reply.  What do you think about reinstall?

Hopefully it will not be required but i have suggested it in the past.

Kind regards

---

### Post by CCitizen on 2012-03-21
Thans guys...

I didnt get any errors and I deleted maverick and natty sources from the directory. However, I did not get any updates... Has it been over 10 days since the last update in ubuntu?

The only PPA I'm really intending to use is Linphone and I2P. Everything else I dont really need.

Also might be good to include a clean slate list of these files and such so people know how a clean directory should be. I been experiementing with different softwares and such on Linux for a while.

---

### Post by matt_symes on 2012-03-21
Hi

If you type

```
sudo apt-get update && sudo apt-get upgrade
```

do you get offered an updates then ? Are there any errors ?

Kind regards

---

### Post by jerrrys on 2012-03-21
Matt: I have a couple of errands to run.  So I leave you with one last thought.   What about wiping it clean?

sudo cp /etc/apt/sources.list.d /etc/apt/sources.list.d.modified

sudo rm /etc/apt/sources.list.d/*

sudo apt-get clean

sudo apt-get update && sudo apt-get upgrade

Good luck CCitizen, hope to hear good news ):P

---

### Post by CCitizen on 2012-03-21
> **matt_symes said:**
> Hi

If you type

```
sudo apt-get update && sudo apt-get upgrade
```do you get offered an updates then ? Are there any errors ?

Kind regards

Didnt see any errors here's what I got

```

Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease             
Ign http://archive.ubuntu.com oneiric-security InRelease            
Ign http://extras.ubuntu.com oneiric InRelease                       
Ign http://archive.canonical.com oneiric InRelease                   
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://archive.ubuntu.com oneiric Release.gpg
Get:1 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]  
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                     
Hit http://ppa.launchpad.net oneiric Release.gpg                     
Get:2 http://archive.ubuntu.com oneiric-security Release.gpg [198 B] 
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                         
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main Sources                              
Get:3 http://archive.ubuntu.com oneiric-updates Release [40.8 kB]    
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:4 http://archive.ubuntu.com oneiric-security Release [40.8 kB]             
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Get:5 http://archive.ubuntu.com oneiric-updates/main Sources [130 kB]          
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA                    
Get:6 http://archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]   
Get:7 http://archive.ubuntu.com oneiric-updates/universe Sources [47.8 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en_CA             
Ign http://extras.ubuntu.com oneiric/main Translation-en_CA                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Get:8 http://archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]   
Get:9 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [300 kB]
Get:10 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:11 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [103 kB]
Get:12 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,202 B]
Get:13 http://archive.ubuntu.com oneiric-updates/main i386 Packages [300 kB]
Get:14 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:15 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [104 kB]
Get:16 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]
Get:17 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:18 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:19 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:20 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:21 http://archive.ubuntu.com oneiric-security/main Sources [34.6 kB]
Get:22 http://archive.ubuntu.com oneiric-security/restricted Sources [14 B]
Get:23 http://archive.ubuntu.com oneiric-security/universe Sources [13.3 kB]
Get:24 http://archive.ubuntu.com oneiric-security/multiverse Sources [1,654 B]
Get:25 http://archive.ubuntu.com oneiric-security/main amd64 Packages [90.3 kB]
Get:26 http://archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:27 http://archive.ubuntu.com oneiric-security/universe amd64 Packages [31.4 kB]
Get:28 http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages [3,194 B]
Get:29 http://archive.ubuntu.com oneiric-security/main i386 Packages [90.5 kB]
Get:30 http://archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:31 http://archive.ubuntu.com oneiric-security/universe i386 Packages [31.4 kB]
Get:32 http://archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,362 B]
Get:33 http://archive.ubuntu.com oneiric-security/main TranslationIndex [73 B]
Get:34 http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:35 http://archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:36 http://archive.ubuntu.com oneiric-security/universe TranslationIndex [73 B]
Get:37 http://archive.ubuntu.com oneiric/main Translation-en_CA [9,465 B]
Hit http://archive.ubuntu.com oneiric/main Translation-en    
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Get:38 http://archive.ubuntu.com oneiric-updates/main Translation-en [141 kB]
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:39 http://archive.ubuntu.com oneiric-updates/universe Translation-en [62.3 kB]
Get:40 http://archive.ubuntu.com oneiric-security/main Translation-en [50.7 kB]
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Get:41 http://archive.ubuntu.com oneiric-security/universe Translation-en [22.1 kB]
Fetched 1,675 kB in 5s (303 kB/s)                                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  thunderbird thunderbird-globalmenu thunderbird-gnome-support
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.9 MB of archives.
After this operation, 864 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main thunderbird-globalmenu amd64 11.0+build1-0ubuntu0.11.10.1 [47.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main thunderbird amd64 11.0+build1-0ubuntu0.11.10.1 [21.8 MB]
Get:3 http://archive.ubuntu.com/ubuntu/ oneiric-updates/main thunderbird-gnome-support amd64 11.0+build1-0ubuntu0.11.10.1 [9,214 B]
Fetched 21.9 MB in 27s (783 kB/s)                                              
(Reading database ... 363118 files and directories currently installed.)
Preparing to replace thunderbird-globalmenu 10.0.2+build1-0ubuntu0.11.10.1 (using .../thunderbird-globalmenu_11.0+build1-0ubuntu0.11.10.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird 10.0.2+build1-0ubuntu0.11.10.1 (using .../thunderbird_11.0+build1-0ubuntu0.11.10.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-gnome-support 10.0.2+build1-0ubuntu0.11.10.1 (using .../thunderbird-gnome-support_11.0+build1-0ubuntu0.11.10.1_amd64.deb) ...
Unpacking replacement thunderbird-gnome-support ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up thunderbird (11.0+build1-0ubuntu0.11.10.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-globalmenu (11.0+build1-0ubuntu0.11.10.1) ...
Setting up thunderbird-gnome-support (11.0+build1-0ubuntu0.11.10.1) ...

```

---

### Post by CCitizen on 2012-03-21
Thanks I dont know if sudo apt-get clean did anything but I got a few updates (thunderbird stuff it seems). Heres hoping update manager starts working again.

I'll give it a day or two and hopefully pick up some updates and mark it as solved then.

---

### Post by CCitizen on 2012-03-23
All fixed i think

---

### Post by jerrrys on 2012-03-23
kool :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

