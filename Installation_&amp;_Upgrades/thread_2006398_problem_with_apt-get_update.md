---
title: "problem with apt-get update"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by kusuma1990 on 2012-06-19
while doing sudo apt-get update

1.    Err [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
  403  Forbidden

2. W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  403  Forbidden

3. E: Some index files failed to download, they have been ignored, or old ones used instead.

atually i want to install kernel source and header files..........

plz help me out as soon as possible :mad:

---

### Post by plucky on 2012-06-19
> **kusuma1990 said:**
> while doing sudo apt-get update

1.    Err [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
  403  Forbidden

2. W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  403  Forbidden

3. E: Some index files failed to download, they have been ignored, or old ones used instead.

atually i want to install kernel source and header files..........

plz help me out as soon as possible :mad:

Could be the repository was offline for maintenance.

When I click on your link, it tries to download a **Packages.gz** file.

Good luck

---

### Post by kusuma1990 on 2012-06-19
what to do now.........?

---

### Post by dino99 on 2012-06-19
> **kusuma1990 said:**
> what to do now.........?

use the genuine ubuntu archives, not exotic ones

---

### Post by kusuma1990 on 2012-06-19
> **dino99 said:**
> use the genuine ubuntu archives, not exotic ones
i am new to ubuntu 

can u plz ellobrate the solution......


i typed sudo apt-get update

so output was

Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg                                 
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-en_IN              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Ign [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
Err [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages                               
  403  Forbidden
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]               
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg [189B]                    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN          
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN    
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN      
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN    
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg [198B]            
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN  
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Get:6 [http://widehat.opensuse.org](http://widehat.opensuse.org) ./ Release.gpg [189B]                        
Ign [http://widehat.opensuse.org/repositories/home:/pstavirs:/ostinato/xUbuntu_10.04/](http://widehat.opensuse.org/repositories/home:/pstavirs:/ostinato/xUbuntu_10.04/) ./ Translation-en_IN
Hit [http://widehat.opensuse.org](http://widehat.opensuse.org) ./ Release                                     
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [417kB]          
Ign [http://widehat.opensuse.org](http://widehat.opensuse.org) ./ Packages                                    
Ign [http://widehat.opensuse.org](http://widehat.opensuse.org) ./ Packages                                    
Hit [http://widehat.opensuse.org](http://widehat.opensuse.org) ./ Packages                                    
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release [57.2kB]                      
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy/free Translation-en_IN                
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy/non-free Translation-en_IN            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Sources                       
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_IN       
Get:10 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                            
Get:11 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,249B]                      
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release [57.3kB]             
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages [1,386kB]              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,855B]  
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [124kB]          
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,259B]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [131kB]     
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [40.8kB]     
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,370B]  
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,316B]   
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:27 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages [617kB]        
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B] 
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources [222kB]         
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]  
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages [270kB]    
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources [101kB]     
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB] 
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources [5,818B]  
Fetched 13.1MB in 22min 14s (9,815B/s)                                         
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://linux.dropbox.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  403  Forbidden

E: Some index files failed to download, they have been ignored, or old ones used instead.


what is the immediate next step that i should take

---

### Post by plucky on 2012-06-19
> i am new to ubuntu

can u plz ellobrate the solution......



Open **Software Sources** and disable the dropbox repository as that is the one giving the problem.It is probably because the line you used was incorrect.

It is in either /etc/apt/sources.list or /etc/apt/sources.list.d

Post output for ```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by kusuma1990 on 2012-06-20
the out put of the vim /etc/apt/source.list is :



# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.;
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

                                                                                                                                                                                                                           1,1           All




and output of /etc/apt/source.list.d/*.list

is deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) lucid main

---

### Post by plucky on 2012-06-20
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free


Those two should be pointing to the lucid repository.

Either edit the file and change hardy to lucid or go [Here](https://help.ubuntu.com/community/Medibuntu) and install the correct repository after you have deleted the original.

For the other problem,open Software Sources and remove dropbox as a source and see if the problem goes away.

Good Luck

---

