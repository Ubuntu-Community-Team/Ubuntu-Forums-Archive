---
title: "Precise 12.04: Fresh install - problem installing misc apps"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by InSearchOf on 2012-04-27
I did a fresh install of 12.04 (64bit) (kept my home-partiton from 10.04 unformatted). Everything seemed good-to-go until I was about to install programs.  In my software center, some apps like Tomboy notes apperars when I search, but they have no install-button. Others again seems to install but get error, like Flashplugin-installer. I have enabled main, universe, restricted and multiverse in software sources.
When installing from terminal I get different error messages, referring to dependencies...

```
sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 flashplugin-installer : Depends: libnspr4-0d but it is not installable
E: Unable to correct problems, you have held broken packages.

```

When I try to install spotify i get this:

```
sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package spotify-client
```


Here's my sources.list:

```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```

And... when I do sudo apt-get update, there seems to be several errors...
```
 sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://repository.spotify.com stable InRelease                             
Ign http://dl.google.com stable InRelease                                      
Ign http://no.archive.ubuntu.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://packages.medibuntu.org precise InRelease                            
Ign http://no.archive.ubuntu.com precise-updates InRelease                     
Ign http://no.archive.ubuntu.com precise-backports InRelease                   
Hit http://no.archive.ubuntu.com precise Release.gpg                           
Hit http://no.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://no.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://no.archive.ubuntu.com precise Release                               
Hit http://no.archive.ubuntu.com precise-updates Release                       
Get:1 http://repository.spotify.com stable Release.gpg [197 B]                 
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://no.archive.ubuntu.com precise-backports Release                     
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://packages.medibuntu.org precise Release.gpg [198 B]                
Get:6 http://repository.spotify.com stable Release [1,765 B]                   
Get:7 http://dl.google.com stable Release [1,347 B]                            
Hit http://no.archive.ubuntu.com precise/main Sources                          
Hit http://no.archive.ubuntu.com precise/restricted Sources                    
Hit http://no.archive.ubuntu.com precise/universe Sources                      
Hit http://no.archive.ubuntu.com precise/multiverse Sources                    
Hit http://no.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://no.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://no.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://no.archive.ubuntu.com precise/main i386 Packages                    
Hit http://no.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://no.archive.ubuntu.com precise/universe i386 Packages                
Hit http://no.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://no.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://no.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://no.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://no.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://no.archive.ubuntu.com precise-updates/main Sources                  
Hit http://no.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://no.archive.ubuntu.com precise-updates/universe Sources              
Hit http://no.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://no.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://no.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://packages.medibuntu.org precise Release                              
Ign http://packages.medibuntu.org precise Release                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://no.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://no.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://no.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://no.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://no.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://no.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://no.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://no.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://no.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://no.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://no.archive.ubuntu.com precise-backports/main Sources                
Hit http://no.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://no.archive.ubuntu.com precise-backports/universe Sources            
Hit http://no.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://no.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://no.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://no.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://no.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://no.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://no.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://no.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://no.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://no.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://no.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://no.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://no.archive.ubuntu.com precise-backports/universe TranslationIndex   
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex    
Get:9 http://security.ubuntu.com precise-security/main Sources [1,550 B]       
Get:10 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Get:11 http://security.ubuntu.com precise-security/universe Sources [2,143 B]  
Get:12 http://security.ubuntu.com precise-security/multiverse Sources [14 B]   
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [12.0 kB]
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [2,552 B]
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [14 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [11.9 kB]
Get:18 http://no.archive.ubuntu.com precise/universe amd64 Packages [6,167 kB] 
Get:19 http://no.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]   
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [2,571 B]
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [14 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://no.archive.ubuntu.com precise/main Translation-en                   
Get:23 http://no.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://no.archive.ubuntu.com precise/multiverse Translation-en             
Get:24 http://no.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]
Hit http://no.archive.ubuntu.com precise/restricted Translation-en             
Get:25 http://no.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://no.archive.ubuntu.com precise/universe Translation-en               
Hit http://no.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://no.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://no.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://no.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://no.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://no.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://no.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://no.archive.ubuntu.com precise-backports/universe Translation-en     
Err http://no.archive.ubuntu.com precise/universe amd64 Packages               
  404  Not Found
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://packages.medibuntu.org precise/non-free TranslationIndex        
Ign http://archive.canonical.com precise/partner Translation-en            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://packages.medibuntu.org precise/free Translation-en_GB               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:26 http://dl.google.com stable Release [1,347 B]                           
Get:27 http://dl.google.com stable/main amd64 Packages [1,244 B]
Get:28 http://dl.google.com stable/main i386 Packages [1,236 B]                
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Fetched 273 kB in 2min 46s (1,640 B/s)
W: GPG error: http://packages.medibuntu.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://repository.spotify.com/dists/stable/Release  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

So... what to do?? :confused:

---

### Post by techsupport on 2012-04-27
I think you might have missed something in the post install process.

Try reviewing a post install guide like this to see what you might have missed:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

> **InSearchOf said:**
> I did a fresh install of 12.04 (64bit) (kept my home-partiton from 10.04 unformatted). Everything seemed good-to-go until I was about to install programs.  In my software center, some apps like Tomboy notes apperars when I search, but they have no install-button. Others again seems to install but get error, like Flashplugin-installer. I have enabled main, universe, restricted and multiverse in software sources.
When installing from terminal I get different error messages, referring to dependencies...

```
sudo apt-get install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 flashplugin-installer : Depends: libnspr4-0d but it is not installable
E: Unable to correct problems, you have held broken packages.

```When I try to install spotify i get this:

```
sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package spotify-client
```
Here's my sources.list:

```
 cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise universe
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
```And... when I do sudo apt-get update, there seems to be several errors...
```
 sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://repository.spotify.com stable InRelease                             
Ign http://dl.google.com stable InRelease                                      
Ign http://no.archive.ubuntu.com precise InRelease                             
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://packages.medibuntu.org precise InRelease                            
Ign http://no.archive.ubuntu.com precise-updates InRelease                     
Ign http://no.archive.ubuntu.com precise-backports InRelease                   
Hit http://no.archive.ubuntu.com precise Release.gpg                           
Hit http://no.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://no.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://no.archive.ubuntu.com precise Release                               
Hit http://no.archive.ubuntu.com precise-updates Release                       
Get:1 http://repository.spotify.com stable Release.gpg [197 B]                 
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://no.archive.ubuntu.com precise-backports Release                     
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://archive.canonical.com precise Release.gpg                           
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:5 http://packages.medibuntu.org precise Release.gpg [198 B]                
Get:6 http://repository.spotify.com stable Release [1,765 B]                   
Get:7 http://dl.google.com stable Release [1,347 B]                            
Hit http://no.archive.ubuntu.com precise/main Sources                          
Hit http://no.archive.ubuntu.com precise/restricted Sources                    
Hit http://no.archive.ubuntu.com precise/universe Sources                      
Hit http://no.archive.ubuntu.com precise/multiverse Sources                    
Hit http://no.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://no.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://no.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Get:8 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://no.archive.ubuntu.com precise/main i386 Packages                    
Hit http://no.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://no.archive.ubuntu.com precise/universe i386 Packages                
Hit http://no.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://no.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://no.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://no.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://no.archive.ubuntu.com precise/universe TranslationIndex             
Hit http://no.archive.ubuntu.com precise-updates/main Sources                  
Hit http://no.archive.ubuntu.com precise-updates/restricted Sources            
Hit http://no.archive.ubuntu.com precise-updates/universe Sources              
Hit http://no.archive.ubuntu.com precise-updates/multiverse Sources            
Hit http://no.archive.ubuntu.com precise-updates/main amd64 Packages           
Hit http://no.archive.ubuntu.com precise-updates/restricted amd64 Packages     
Hit http://packages.medibuntu.org precise Release                              
Ign http://packages.medibuntu.org precise Release                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://no.archive.ubuntu.com precise-updates/universe amd64 Packages       
Hit http://no.archive.ubuntu.com precise-updates/multiverse amd64 Packages     
Hit http://no.archive.ubuntu.com precise-updates/main i386 Packages            
Hit http://no.archive.ubuntu.com precise-updates/restricted i386 Packages      
Hit http://no.archive.ubuntu.com precise-updates/universe i386 Packages        
Hit http://no.archive.ubuntu.com precise-updates/multiverse i386 Packages      
Hit http://no.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://no.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://no.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://no.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://no.archive.ubuntu.com precise-backports/main Sources                
Hit http://no.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://no.archive.ubuntu.com precise-backports/universe Sources            
Hit http://no.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://no.archive.ubuntu.com precise-backports/main amd64 Packages         
Hit http://no.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://no.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://no.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://no.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://no.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://no.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://no.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://no.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://no.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://no.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://no.archive.ubuntu.com precise-backports/universe TranslationIndex   
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex    
Get:9 http://security.ubuntu.com precise-security/main Sources [1,550 B]       
Get:10 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Get:11 http://security.ubuntu.com precise-security/universe Sources [2,143 B]  
Get:12 http://security.ubuntu.com precise-security/multiverse Sources [14 B]   
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [12.0 kB]
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [2,552 B]
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [14 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [11.9 kB]
Get:18 http://no.archive.ubuntu.com precise/universe amd64 Packages [6,167 kB] 
Get:19 http://no.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]   
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [2,571 B]
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [14 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://no.archive.ubuntu.com precise/main Translation-en                   
Get:23 http://no.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://no.archive.ubuntu.com precise/multiverse Translation-en             
Get:24 http://no.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]
Hit http://no.archive.ubuntu.com precise/restricted Translation-en             
Get:25 http://no.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Hit http://no.archive.ubuntu.com precise/universe Translation-en               
Hit http://no.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://no.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://no.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://no.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://no.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://no.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Hit http://no.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://no.archive.ubuntu.com precise-backports/universe Translation-en     
Err http://no.archive.ubuntu.com precise/universe amd64 Packages               
  404  Not Found
Ign http://archive.canonical.com precise/partner Translation-en_GB             
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://packages.medibuntu.org precise/non-free TranslationIndex        
Ign http://archive.canonical.com precise/partner Translation-en            
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign http://packages.medibuntu.org precise/free Translation-en_GB               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign http://packages.medibuntu.org precise/non-free Translation-en_GB
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:26 http://dl.google.com stable Release [1,347 B]                           
Get:27 http://dl.google.com stable/main amd64 Packages [1,244 B]
Get:28 http://dl.google.com stable/main i386 Packages [1,236 B]                
Ign http://dl.google.com stable/main TranslationIndex
Ign http://dl.google.com stable/main Translation-en_GB
Ign http://dl.google.com stable/main Translation-en
Fetched 273 kB in 2min 46s (1,640 B/s)
W: GPG error: http://packages.medibuntu.org precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://repository.spotify.com/dists/stable/Release  Unable to find expected entry 'non-free/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://no.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```So... what to do?? :confused:

---

### Post by InSearchOf on 2012-04-27
Thanks, but can't seem to find anything I should've done :\

---

### Post by InSearchOf on 2012-04-27
Hmm.. seemed to work after changing download server in software sources.

---

