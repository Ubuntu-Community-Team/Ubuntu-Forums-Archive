---
title: "Can't get updates"
date: 2012-03-14
forum: Installation &amp; Upgrades
---

### Post by hodad on 2012-03-14
11.10 Upgrade Center doesn't work.  Progress bar jerks around and the posts Error:
"Failed to download repository information"

followed by:

W:Failed to fetch [http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I also can't find the instructions for doing it via "sudo apt-get install", which also doesn't seem to want to work.

Any suggestions? Thanks

---

### Post by cortman on 2012-03-14
Please post the output of 

```
sudo apt-get update
```

and

```
cat /etc/apt/sources.list
```

---

### Post by hodad on 2012-03-28
dave@DavesLinuxBox:~$ sudo apt-get update
[sudo] password for dave: 
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                               
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric Release.gpg                                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                             
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric Release                                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                          
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric/extra TranslationIndex                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Err [http://www.bchemnet.com](http://www.bchemnet.com) oneiric/extra i386 Packages              
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en                  
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric/extra Translation-en_US                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://www.bchemnet.com](http://www.bchemnet.com) oneiric/extra Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
W: Failed to fetch [http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
dave@DavesLinuxBox:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) oneiric extra

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
dave@DavesLinuxBox:~$ ^C
dave@DavesLinuxBox:~$

---

### Post by plucky on 2012-03-29
Open **Software Sources > Other Software** Tag and un-tick the entry for [http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages](http://www.bchemnet.com/suldr/dists/oneiric/extra/binary-i386/Packages) and then see if the 404 erros go away.


Or remove the .list file from /etc/apt/sources.list.d/

Good Luck

---

### Post by peterlauri on 2012-03-29
I can confirm the same problem for me. I just started a few hours ago, was hoping it to be fixed by now :)

```
plauri@pjotr-ubuntu:~$ sudo apt-get update 2>&1 | tee ~/apt-get-update.out
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://CRAN.R-project.org oneiric/ InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease
Ign http://archive.ubuntu.com oneiric-backports InRelease
Ign http://archive.canonical.com oneiric InRelease
Ign http://dl.google.com stable InRelease
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Ign http://archive.ubuntu.com oneiric-security InRelease
Get:2 http://CRAN.R-project.org oneiric/ Release.gpg [490 B]
Ign http://downloads-distro.mongodb.org dist InRelease
Ign http://download.virtualbox.org oneiric InRelease
Hit http://archive.ubuntu.com oneiric Release.gpg
Get:3 http://archive.canonical.com oneiric Release.gpg [198 B]
Get:4 http://dl.google.com stable Release.gpg [198 B]
Hit http://extras.ubuntu.com oneiric Release
Ign http://extras.ubuntu.com oneiric Release
Ign http://www.rabbitmq.com testing InRelease
Hit http://CRAN.R-project.org oneiric/ Release
Hit http://archive.canonical.com oneiric Release
Hit http://archive.ubuntu.com oneiric-updates Release.gpg
Hit http://archive.ubuntu.com oneiric-backports Release.gpg
Ign http://CRAN.R-project.org oneiric/ Release
Ign http://archive.canonical.com oneiric Release
Get:5 http://dl.google.com stable Release [1,347 B]
Ign http://extras.ubuntu.com oneiric/main Sources/DiffIndex
Get:6 http://downloads-distro.mongodb.org dist Release.gpg [490 B]
Get:7 http://download.virtualbox.org oneiric Release.gpg [197 B]
Hit http://archive.ubuntu.com oneiric-security Release.gpg
Ign http://CRAN.R-project.org oneiric/ Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex
Ign http://extras.ubuntu.com oneiric/main amd64 Packages/DiffIndex
Ign http://extras.ubuntu.com oneiric/main i386 Packages/DiffIndex
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Get:8 http://dl.google.com stable/main amd64 Packages [1,237 B]
Hit http://archive.ubuntu.com oneiric Release
Hit http://archive.ubuntu.com oneiric-updates Release
Get:9 http://www.rabbitmq.com testing Release.gpg [197 B]
Ign http://archive.canonical.com oneiric/partner amd64 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner i386 Packages/DiffIndex
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://downloads-distro.mongodb.org dist Release
Hit http://download.virtualbox.org oneiric Release
Ign http://downloads-distro.mongodb.org dist Release
Ign http://download.virtualbox.org oneiric Release
Hit http://archive.ubuntu.com oneiric-backports Release
Hit http://archive.canonical.com oneiric/partner Sources
Hit http://extras.ubuntu.com oneiric/main amd64 Packages
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Hit http://archive.ubuntu.com oneiric-security Release
Hit http://archive.ubuntu.com oneiric/main Sources
Hit http://archive.ubuntu.com oneiric/restricted Sources
Get:10 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]
Ign http://downloads-distro.mongodb.org dist/10gen amd64 Packages/DiffIndex
Ign http://download.virtualbox.org oneiric/contrib amd64 Packages/DiffIndex
Hit http://www.rabbitmq.com testing Release
Ign http://www.rabbitmq.com testing Release
Get:11 http://archive.canonical.com oneiric/partner amd64 Packages [3,554 B]
Get:12 http://archive.canonical.com oneiric/partner i386 Packages [4,329 B]
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
Ign http://downloads-distro.mongodb.org dist/10gen i386 Packages/DiffIndex
Ign http://downloads-distro.mongodb.org dist/10gen TranslationIndex
Ign http://download.virtualbox.org oneiric/contrib i386 Packages/DiffIndex
Ign http://www.rabbitmq.com testing/main amd64 Packages/DiffIndex
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex
Ign http://www.rabbitmq.com testing/main i386 Packages/DiffIndex
Hit http://archive.ubuntu.com oneiric/universe Sources
Hit http://archive.ubuntu.com oneiric/main amd64 Packages
Get:13 http://archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]
Hit http://download.virtualbox.org oneiric/contrib amd64 Packages
Get:14 http://archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]
Ign http://www.rabbitmq.com testing/main TranslationIndex
Hit http://download.virtualbox.org oneiric/contrib i386 Packages
Get:15 http://dl.google.com stable/main i386 Packages [1,244 B]
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric/main i386 Packages
Get:16 http://archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]
Get:17 http://archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://CRAN.R-project.org oneiric/ Packages
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://CRAN.R-project.org oneiric/ Translation-en_US
Err http://archive.canonical.com oneiric/partner amd64 Packages
  404  Not Found [IP: 91.189.92.191 80]
Err http://archive.canonical.com oneiric/partner i386 Packages
  404  Not Found [IP: 91.189.92.191 80]
Ign http://CRAN.R-project.org oneiric/ Translation-en
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Get:18 http://archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:19 http://archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://dl.google.com stable/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/main Sources
Get:20 http://archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Get:21 http://archive.ubuntu.com oneiric-updates/multiverse Sources [3,661 B]
Hit http://archive.ubuntu.com oneiric-updates/universe Sources
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages
Ign http://archive.canonical.com oneiric/partner Translation-en
Get:22 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [2,982 B]
Get:23 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [6,210 B]
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages
Get:24 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:25 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,356 B]
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex
Get:26 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:27 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/main Sources
Hit http://archive.ubuntu.com oneiric-backports/universe Sources
Get:28 http://archive.ubuntu.com oneiric-backports/restricted Sources [14 B]
Get:29 http://archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]
Hit http://archive.ubuntu.com oneiric-backports/main amd64 Packages
Hit http://archive.ubuntu.com oneiric-backports/universe amd64 Packages
Get:30 http://archive.ubuntu.com oneiric-backports/restricted amd64 Packages [14 B]
Get:31 http://archive.ubuntu.com oneiric-backports/multiverse amd64 Packages [14 B]
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages
Get:32 http://archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]
Get:33 http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex
Get:34 http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex [70 B]
Get:35 http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex [70 B]
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/main Sources
Get:36 http://archive.ubuntu.com oneiric-security/restricted Sources [14 B]
Get:37 http://archive.ubuntu.com oneiric-security/multiverse Sources [1,638 B]
Hit http://archive.ubuntu.com oneiric-security/universe Sources
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages
Get:38 http://downloads-distro.mongodb.org dist/10gen amd64 Packages [947 B]
Get:39 http://archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:40 http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages [3,211 B]
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages
Get:41 http://archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:42 http://archive.ubuntu.com oneiric-security/multiverse i386 Packages [3,372 B]
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex
Get:43 http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex [72 B]
Get:44 http://archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en
Get:45 http://archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]
Get:46 http://downloads-distro.mongodb.org dist/10gen i386 Packages [945 B]
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US
Get:47 http://www.rabbitmq.com testing/main amd64 Packages [489 B]
Get:48 http://archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en
Get:49 http://archive.ubuntu.com oneiric-updates/multiverse Translation-en [3,524 B]
Get:50 http://archive.ubuntu.com oneiric-updates/restricted Translation-en [508 B]
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en
Get:51 http://archive.ubuntu.com oneiric-backports/multiverse Translation-en [14 B]
Get:52 http://archive.ubuntu.com oneiric-backports/restricted Translation-en [14 B]
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en_US
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Get:53 http://archive.ubuntu.com oneiric-security/multiverse Translation-en [1,494 B]
Hit http://www.rabbitmq.com testing/main i386 Packages
Ign http://downloads-distro.mongodb.org dist/10gen Translation-en
Get:54 http://archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
Ign http://download.virtualbox.org oneiric/contrib Translation-en
Ign http://dl.google.com stable/main Translation-en_US
Ign http://dl.google.com stable/main Translation-en
Ign http://www.rabbitmq.com testing/main Translation-en_US
Ign http://www.rabbitmq.com testing/main Translation-en
Fetched 544 kB in 5s (95.8 kB/s)
W: GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://CRAN.R-project.org oneiric/ Release: The following signatures were invalid: BADSIG 51716619E084DAB9 Michael Rutter <marutter@gmail.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://downloads-distro.mongodb.org dist Release: The following signatures were invalid: BADSIG 9ECBEC467F0CEB10 Richard Kreuter <richard@10gen.com>
W: GPG error: http://download.virtualbox.org oneiric Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
W: GPG error: http://www.rabbitmq.com testing Release: The following signatures were invalid: BADSIG F7B8CEA6056E8E56 RabbitMQ Release Signing Key <info@rabbitmq.com>
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-amd64/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages  404  Not Found [IP: 91.189.92.191 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-amd64_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/downloads-distro.mongodb.org_repo_ubuntu-upstart_dists_dist_10gen_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.rabbitmq.com_debian_dists_testing_main_binary-amd64_Packages  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by desi on 2012-03-29
Same error message as the original post.
When i tried to edit source file I get the following:

gksu gedit /etc/apt/sources.list

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:226:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:532:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:537:21: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:764:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:810:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:829:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:842:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1028:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1215:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1311:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1461:21: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1660:22: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1698:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1821:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1945:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2005:24: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2055:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2062:22: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2076:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:4:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:10:18: 'inherit' is not a valid color name

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:17:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:22:17: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:25:35: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:28:29: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:31:16: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:34:28: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:37:19: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:48:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:55:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:67:29: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:80:20: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:105:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:126:23: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:144:29: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:162:28: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:181:24: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:200:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:213:31: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:226:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:239:36: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:246:14: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:252:23: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:255:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:258:24: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:261:21: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:278:28: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:301:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:306:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:312:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:348:28: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:379:27: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:389:34: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:411:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:422:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:439:36: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:453:46: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:460:43: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:473:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:489:24: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:496:23: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:504:27: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:515:44: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:523:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:529:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:535:39: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:557:20: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:568:14: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:571:17: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:574:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:577:15: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:583:17: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:591:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:595:29: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:598:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:604:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:626:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:640:42: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:653:44: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:666:16: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:680:25: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:690:24: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:694:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:698:36: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:702:33: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:706:39: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:710:45: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:714:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:720:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:726:19: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:732:27: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:739:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:746:39: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:753:49: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:760:28: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:763:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:770:17: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:774:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:778:24: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:784:34: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:792:50: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:800:27: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:813:20: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:820:22: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:829:21: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:835:18: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:844:25: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:860:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:876:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:892:25: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:905:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:914:20: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:921:17: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:926:25: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:944:38: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:948:37: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:974:41: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:978:41: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:999:60: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1006:60: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1023:40: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1038:46: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1051:52: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1064:45: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1074:52: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1084:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1097:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1106:44: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1113:40: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1121:46: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1133:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1146:48: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1153:40: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1173:49: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1183:54: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1197:57: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1204:56: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1215:27: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: gtk-widgets-backdrop.css:1221:26: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:8:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:57:30: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:80:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:92:20: Junk at end of value

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:114:32: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:125:45: Unknown pseudo-class 'backdrop'

(gedit:9974): Gtk-WARNING **: Theme parsing error: nautilus.css:148:39: Unknown pseudo-class 'backdrop'
If I try to open Software Sources, that window appears for a fraction of a second and then disappears.
Any help, please?

---

### Post by peterlauri on 2012-03-29
I solved this by running these commands. But I'm not sure if it can damage YOUR setup.

```

# sudo apt-get clean
# sudo rm /var/lib/apt/lists/*
# sudo rm /var/lib/apt/lists/partial/*
# sudo apt-get clean
# sudo apt-get update

```

---

### Post by hodad on 2012-03-29
Thanks for the idea.
I tried a similar path, but that's what started the problem, so...

I already went down the path of reinstalling 11.10.  In the process of doing that now, but am having some sort of crazy MOBO problem.   Seems I have multiple problems, which always adds to the fun.

---

