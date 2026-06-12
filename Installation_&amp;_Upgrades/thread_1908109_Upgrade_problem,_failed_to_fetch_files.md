---
title: "Upgrade problem, failed to fetch files"
date: 2012-01-12
forum: Installation &amp; Upgrades
---

### Post by combustibleChole on 2012-01-12
Hey all, I'm new-ish to ubuntu/linux and have just gotten a systems76 machine running 11.10.  It seemed to be updating fine the first few days, but now it's giving all sorts of error messages when updating.  It appears that I can't update at all through the update manager (error reads check your internet connection even when I've got a great connection), and the terminal gives me the following errors: 

```
W: Failed to fetch http://archive.canonical.com/dists/oneiric/Release  Unable to find expected entry 'patner/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Here is the whole output from my terminal update session:

```
sudo apt-get update && apt-get upgrade
[sudo] password for chole: 
Ign http://mirror.hmc.edu oneiric InRelease
Ign http://mirror.hmc.edu oneiric-updates InRelease                            
Ign http://dl.google.com stable InRelease                                      
Ign http://mirror.hmc.edu oneiric-backports InRelease                          
Ign http://mirror.hmc.edu oneiric-security InRelease                           
Hit http://mirror.hmc.edu oneiric Release.gpg                                  
Hit http://mirror.hmc.edu oneiric-updates Release.gpg                          
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://mirror.hmc.edu oneiric-backports Release.gpg                        
Hit http://mirror.hmc.edu oneiric-security Release.gpg                         
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://mirror.hmc.edu oneiric Release                                      
Hit http://mirror.hmc.edu oneiric-updates Release                              
Hit http://mirror.hmc.edu oneiric-backports Release                            
Ign http://planet76.com ./ InRelease                                           
Hit http://mirror.hmc.edu oneiric-security Release                             
Hit http://mirror.hmc.edu oneiric/main Sources                                 
Get:3 http://dl.google.com stable/main amd64 Packages [748 B]                  
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:4 http://planet76.com ./ Release.gpg [198 B]                               
Hit http://mirror.hmc.edu oneiric/restricted Sources                           
Hit http://mirror.hmc.edu oneiric/universe Sources                             
Hit http://mirror.hmc.edu oneiric/multiverse Sources                           
Hit http://mirror.hmc.edu oneiric/main amd64 Packages                          
Hit http://mirror.hmc.edu oneiric/restricted amd64 Packages                    
Hit http://mirror.hmc.edu oneiric/universe amd64 Packages                      
Hit http://mirror.hmc.edu oneiric/multiverse amd64 Packages                    
Hit http://mirror.hmc.edu oneiric/main i386 Packages                           
Hit http://mirror.hmc.edu oneiric/restricted i386 Packages                     
Hit http://mirror.hmc.edu oneiric/universe i386 Packages                       
Get:5 http://dl.google.com stable/main i386 Packages [765 B]                   
Hit http://mirror.hmc.edu oneiric/multiverse i386 Packages                     
Hit http://mirror.hmc.edu oneiric/main TranslationIndex                        
Hit http://planet76.com ./ Release                                             
Hit http://mirror.hmc.edu oneiric/multiverse TranslationIndex                  
Hit http://mirror.hmc.edu oneiric/restricted TranslationIndex                  
Hit http://mirror.hmc.edu oneiric/universe TranslationIndex                    
Hit http://mirror.hmc.edu oneiric-updates/main Sources                         
Hit http://mirror.hmc.edu oneiric-updates/restricted Sources                   
Hit http://mirror.hmc.edu oneiric-updates/universe Sources                     
Hit http://mirror.hmc.edu oneiric-updates/multiverse Sources                   
Hit http://mirror.hmc.edu oneiric-updates/main amd64 Packages                  
Hit http://mirror.hmc.edu oneiric-updates/restricted amd64 Packages            
Hit http://mirror.hmc.edu oneiric-updates/universe amd64 Packages              
Hit http://mirror.hmc.edu oneiric-updates/multiverse amd64 Packages            
Hit http://mirror.hmc.edu oneiric-updates/main i386 Packages                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:6 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:7 http://ppa.launchpad.net oneiric Release.gpg [316 B]                     
Hit http://planet76.com ./ Packages                                            
Hit http://mirror.hmc.edu oneiric-updates/restricted i386 Packages             
Hit http://mirror.hmc.edu oneiric-updates/universe i386 Packages               
Hit http://mirror.hmc.edu oneiric-updates/multiverse i386 Packages             
Hit http://mirror.hmc.edu oneiric-updates/main TranslationIndex                
Hit http://mirror.hmc.edu oneiric-updates/multiverse TranslationIndex          
Hit http://mirror.hmc.edu oneiric-updates/restricted TranslationIndex          
Hit http://mirror.hmc.edu oneiric-updates/universe TranslationIndex            
Hit http://mirror.hmc.edu oneiric-backports/main Sources                       
Hit http://mirror.hmc.edu oneiric-backports/restricted Sources                 
Hit http://mirror.hmc.edu oneiric-backports/universe Sources                   
Hit http://mirror.hmc.edu oneiric-backports/multiverse Sources                 
Hit http://mirror.hmc.edu oneiric-backports/main amd64 Packages                
Hit http://mirror.hmc.edu oneiric-backports/restricted amd64 Packages          
Hit http://mirror.hmc.edu oneiric-backports/universe amd64 Packages            
Hit http://mirror.hmc.edu oneiric-backports/multiverse amd64 Packages          
Hit http://mirror.hmc.edu oneiric-backports/main i386 Packages                 
Hit http://mirror.hmc.edu oneiric-backports/restricted i386 Packages           
Hit http://mirror.hmc.edu oneiric-backports/universe i386 Packages             
Hit http://mirror.hmc.edu oneiric-backports/multiverse i386 Packages           
Hit http://mirror.hmc.edu oneiric-backports/main TranslationIndex              
Hit http://mirror.hmc.edu oneiric-backports/multiverse TranslationIndex        
Hit http://mirror.hmc.edu oneiric-backports/restricted TranslationIndex        
Hit http://mirror.hmc.edu oneiric-backports/universe TranslationIndex          
Hit http://mirror.hmc.edu oneiric-security/main Sources                        
Hit http://mirror.hmc.edu oneiric-security/restricted Sources                  
Hit http://mirror.hmc.edu oneiric-security/universe Sources                    
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://mirror.hmc.edu oneiric-security/multiverse Sources                  
Hit http://mirror.hmc.edu oneiric-security/main amd64 Packages                 
Hit http://mirror.hmc.edu oneiric-security/restricted amd64 Packages           
Hit http://mirror.hmc.edu oneiric-security/universe amd64 Packages             
Hit http://mirror.hmc.edu oneiric-security/multiverse amd64 Packages           
Hit http://mirror.hmc.edu oneiric-security/main i386 Packages                  
Hit http://mirror.hmc.edu oneiric-security/restricted i386 Packages            
Hit http://mirror.hmc.edu oneiric-security/universe i386 Packages              
Hit http://mirror.hmc.edu oneiric-security/multiverse i386 Packages            
Hit http://mirror.hmc.edu oneiric-security/main TranslationIndex               
Hit http://mirror.hmc.edu oneiric-security/multiverse TranslationIndex         
Hit http://mirror.hmc.edu oneiric-security/restricted TranslationIndex         
Hit http://mirror.hmc.edu oneiric-security/universe TranslationIndex           
Hit http://mirror.hmc.edu oneiric/main Translation-en_GB                       
Hit http://mirror.hmc.edu oneiric/main Translation-en                          
Hit http://mirror.hmc.edu oneiric/multiverse Translation-en_GB                 
Hit http://mirror.hmc.edu oneiric/multiverse Translation-en                    
Hit http://mirror.hmc.edu oneiric/restricted Translation-en_GB                 
Hit http://mirror.hmc.edu oneiric/restricted Translation-en                    
Hit http://mirror.hmc.edu oneiric/universe Translation-en_GB                   
Hit http://mirror.hmc.edu oneiric/universe Translation-en                      
Hit http://mirror.hmc.edu oneiric-updates/main Translation-en                  
Hit http://mirror.hmc.edu oneiric-updates/multiverse Translation-en            
Hit http://archive.canonical.com oneiric Release                               
Hit http://mirror.hmc.edu oneiric-updates/restricted Translation-en            
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://mirror.hmc.edu oneiric-updates/universe Translation-en              
Hit http://mirror.hmc.edu oneiric-backports/main Translation-en                
Hit http://mirror.hmc.edu oneiric-backports/multiverse Translation-en          
Hit http://mirror.hmc.edu oneiric-backports/restricted Translation-en          
Hit http://mirror.hmc.edu oneiric-backports/universe Translation-en            
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://mirror.hmc.edu oneiric-security/main Translation-en                 
Hit http://mirror.hmc.edu oneiric-security/multiverse Translation-en           
Hit http://mirror.hmc.edu oneiric-security/restricted Translation-en           
Hit http://mirror.hmc.edu oneiric-security/universe Translation-en             
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Ign http://planet76.com ./ Translation-en_GB                                   
Ign http://planet76.com ./ Translation-en                            
Hit http://archive.canonical.com oneiric/partner Sources             
Hit http://archive.canonical.com oneiric/partner amd64 Packages      
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Ign http://planet76.com ./ Translation-en_US                         
Ign http://archive.canonical.com oneiric/partner TranslationIndex    
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB
Ign http://ppa.launchpad.net oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://archive.canonical.com oneiric/partner Translation-en_GB
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Fetched 3,644 B in 4s (862 B/s)
W: Failed to fetch http://archive.canonical.com/dists/oneiric/Release  Unable to find expected entry 'patner/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

And here's my sources.list file:
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.hmc.edu/ubuntu/ oneiric main restricted
deb-src http://mirror.hmc.edu/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.hmc.edu/ubuntu/ oneiric-updates main restricted
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.hmc.edu/ubuntu/ oneiric universe
deb-src http://mirror.hmc.edu/ubuntu/ oneiric universe
deb http://mirror.hmc.edu/ubuntu/ oneiric-updates universe
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.hmc.edu/ubuntu/ oneiric multiverse
deb-src http://mirror.hmc.edu/ubuntu/ oneiric multiverse
deb http://mirror.hmc.edu/ubuntu/ oneiric-updates multiverse
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.hmc.edu/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://mirror.hmc.edu/ubuntu/ oneiric-security main restricted
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-security main restricted
deb http://mirror.hmc.edu/ubuntu/ oneiric-security universe
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-security universe
deb http://mirror.hmc.edu/ubuntu/ oneiric-security multiverse
deb-src http://mirror.hmc.edu/ubuntu/ oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
deb http://archive.canonical.com/ oneiric patner
deb-src http://archive.canonical.com/ oneiric patner
```

I've tried to change servers, several times, all with the same errors.  I've also tried recommendations from other threads to no avail.

Thanks in advance for your help,
cCh.

---

### Post by Old_Grey_Wolf on 2012-01-12
At the bottom of the sources.list file there are two lines
> deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric patner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric patner

Note the typo "patner" versus "partner".

Remove those two lines and save the file. They are malformed versions of these lines you have 6 lines above them in the sources.list file > deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

Post back here if you still have problems updating.

---

### Post by combustibleChole on 2012-01-13
Appears to have worked, for now at least.  Still some errors while trying to update through the terminal, however, the update manager is working now!

Thanks so much, I'm awful at catching typos like that, especially in code I didn't write.

-cCh

---

### Post by Old_Grey_Wolf on 2012-01-14
Let's try to resolve the other errors you are getting.

Enter this command and post the output ```
sudo apt-get update
``` Then enter this command and post the output ```
sudo apt-get upgrade
```

---

### Post by combustibleChole on 2012-01-15
hrm. So, no errors when I enter the commands separately, but when I use ```
sudo apt-get update && apt-get upgrade
```

I get

```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

I wonder what that's about.  I was under the (possibly mistaken) impression that was an okay command.  I mean, I'm learning all this stuff over the internet, which is /totally always right/.

---

### Post by Old_Grey_Wolf on 2012-01-15
If you don't have apt, synaptic, or software center open at the same time then enter this command to remove the lock-file ```
sudo rm /var/lib/dpkg/lock
```

Edit: Ignore this post and read the next one. You had an error in the command you entered.

---

### Post by Old_Grey_Wolf on 2012-01-16
Also the command you entered has a sudo missing it should be ```
sudo apt-get update && sudo apt-get upgrade
```

---

