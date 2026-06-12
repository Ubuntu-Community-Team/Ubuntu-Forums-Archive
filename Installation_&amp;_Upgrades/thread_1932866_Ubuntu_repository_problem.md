---
title: "Ubuntu repository problem"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by darjeelingtee on 2012-02-28
Hi all,

Having recently edited my sources.list to include medibuntu (I know  a dangerous thing to do when you don't completely know what you are doing!) I appear to have caused a number of problems so that I now cannot update my system or indeed install new applications (my intention is to install build-essential so that I can compile Octave 3.4.3 in Ubuntu 11.10).

My system details are as follows:
Ubuntu 11.10 64 bit
AMD E-350 x2

```
sudo apt-get update
``` results in the terminal getting stuck and not downloading anything.

```
sudo apt-get install build-essential
``` results in:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ oneiric/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ oneiric/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ oneiric/free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_free_binary-i386_Packages)
W: Duplicate sources.list entry http://packages.medibuntu.org/ oneiric/non-free i386 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Package 'build-essential' has no installation candidate

```

Clearly I have duplicate entries but I have tried generating sources list from [http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/") but that doesnt work either. Below is my current sources.list. Any help would be great.
```
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386]/ oneiric main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Medibuntu - Ubuntu 11.10 "Oneiric Ocelot"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ oneiric free non-free
deb-src http://packages.medibuntu.org/ oneiric free non-free

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free

```

Cheers, Matt

Update:
So I am now running as simple a source.list as I think possible:
```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://se.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 
deb-src http://se.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://se.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb http://se.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
deb http://se.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse 
deb http://se.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse 
deb-src http://se.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse 
deb-src http://se.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse 
deb-src http://se.archive.ubuntu.com/ubuntu/ oneiric-proposed main restricted universe multiverse 
deb-src http://se.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse 

```
but 
```
sudo apt-get update
``` just gets stuck at the following:
```
Ign http://se.archive.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://se.archive.ubuntu.com oneiric-security InRelease                    
Ign http://se.archive.ubuntu.com oneiric-updates InRelease           
Ign http://se.archive.ubuntu.com oneiric-proposed InRelease          
Ign http://se.archive.ubuntu.com oneiric-backports InRelease         
Hit http://packages.medibuntu.org oneiric InRelease                  
Get:1 http://se.archive.ubuntu.com oneiric Release.gpg [198 B]       
Get:2 http://se.archive.ubuntu.com oneiric-security Release.gpg [198 B]
Get:3 http://se.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://archive.canonical.com oneiric Release.gpg                           
Get:4 http://se.archive.ubuntu.com oneiric-proposed Release.gpg [198 B]        
Get:5 http://se.archive.ubuntu.com oneiric-backports Release.gpg [198 B]       
Ign http://ppa.launchpad.net oneiric InRelease                       
Hit http://se.archive.ubuntu.com oneiric Release                               
Get:6 http://se.archive.ubuntu.com oneiric-security Release [40.8 kB]          
Ign http://se.archive.ubuntu.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:7 http://se.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://packages.medibuntu.org oneiric/free amd64 Packages                  
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://ppa.launchpad.net oneiric Release                                
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://packages.medibuntu.org oneiric/non-free amd64 Packages              
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                  
Hit http://ppa.launchpad.net oneiric/main Sources                           
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                    
Hit http://ppa.launchpad.net oneiric/main i386 Packages                     
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                  
Hit http://ppa.launchpad.net oneiric/main Sources                           
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                 
Ign http://ppa.launchpad.net oneiric/main Translation-en                    
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                 
Ign http://ppa.launchpad.net oneiric/main Translation-en                    
Ign http://packages.medibuntu.org oneiric/free TranslationIndex             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Ign http://archive.canonical.com oneiric/partner Translation-en_GB          
Ign http://archive.canonical.com oneiric/partner Translation-en
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/free Translation-en
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB
Ign http://packages.medibuntu.org oneiric/non-free Translation-en              
Get:8 http://se.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
Get:9 http://se.archive.ubuntu.com oneiric-updates Release [40.8 kB]           
51% [9 Release 915 B/40.8 kB 2%]
```

Cheers, Matt

---

### Post by plucky on 2012-02-28
Post output of ```
ls -l /etc/apt/sources.list.d/
```

> W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

I don't see another entry in your sources.list so it must also be in sources.list.d directory.

> W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric/free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) oneiric/non-free amd64 Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_oneiric_non-free_binary-amd64_Packages)

Put a # in front of the medibuntu entries in your sources.list file.

You can also put a # in front of all the lines that start with deb-src as you don't really need the source code entries.


> Code:

sudo apt-get update

results in the terminal getting stuck and not downloading anything.


What do you mean "getting stuck"?

---

### Post by darjeelingtee on 2012-02-28
The output of ```
ls -l /etc/apt/sources.list.d/
``` is
```
total 48
-rw-r--r-- 1 root root 281 2012-02-27 14:45 medibuntu.list
-rw-r--r-- 1 root root 281 2012-02-27 14:41 medibuntu.list.save
-rw-r--r-- 1 root root  82 2012-02-27 14:45 oneiric-partner.list
-rw-r--r-- 1 root root  82 2012-02-27 14:41 oneiric-partner.list.save
-rw-r--r-- 1 root root 144 2012-02-27 14:45 scopes-packagers-ppa-oneiric.list
-rw-r--r-- 1 root root 144 2012-02-27 14:41 scopes-packagers-ppa-oneiric.list.save
-rw-r--r-- 1 root root 130 2012-02-27 14:45 tualatrix-ppa-oneiric.list
-rw-r--r-- 1 root root 130 2012-02-27 14:41 tualatrix-ppa-oneiric.list.save
-rw-r--r-- 1 root root 134 2012-02-27 14:45 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root 134 2012-02-27 14:41 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root 118 2012-02-27 14:45 wfg-0ad-oneiric.list
-rw-r--r-- 1 root root 118 2012-02-27 14:41 wfg-0ad-oneiric.list.save

```
Presumably there is some sort of mismatch here?
I will put a # in front of the deb-src entries as you suggest

When I say getting stuck I mean nothing further will occur, even if I leave it for hours. The terminal will remain at this point with no downloads etc.

Thanks, Matt

---

### Post by plucky on 2012-02-28
> -rw-r--r-- 1 root root 281 2012-02-27 14:45 medibuntu.list
-rw-r--r-- 1 root root 281 2012-02-27 14:41 medibuntu.list.save
-rw-r--r-- 1 root root  82 2012-02-27 14:45 oneiric-partner.list
-rw-r--r-- 1 root root  82 2012-02-27 14:41 oneiric-partner.list.save

That is why you are getting the duplicate entries.

The Medibuntu repository should be in /etc/apt/sources.list.d,but the partner repository should be in sources.list.

So delete the entries for Medibuntu in sources.list and delete the partner lists in sources.list.d.

Good Luck

---

### Post by darjeelingtee on 2012-02-28
OK thanks so I have done as you suggested and my sources.list is now as follows:
```
#deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386]/ oneiric main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

# Google software repository
deb http://dl.google.com/linux/deb/ stable non-free
``` and my sources.list.d is as follows:
```
total 40
-rw-r--r-- 1 root root 281 2012-02-27 14:45 medibuntu.list
-rw-r--r-- 1 root root 281 2012-02-27 14:41 medibuntu.list.save
-rw-r--r-- 1 root root 144 2012-02-27 14:45 scopes-packagers-ppa-oneiric.list
-rw-r--r-- 1 root root 144 2012-02-27 14:41 scopes-packagers-ppa-oneiric.list.save
-rw-r--r-- 1 root root 130 2012-02-27 14:45 tualatrix-ppa-oneiric.list
-rw-r--r-- 1 root root 130 2012-02-27 14:41 tualatrix-ppa-oneiric.list.save
-rw-r--r-- 1 root root 134 2012-02-27 14:45 ubuntu-wine-ppa-oneiric.list
-rw-r--r-- 1 root root 134 2012-02-27 14:41 ubuntu-wine-ppa-oneiric.list.save
-rw-r--r-- 1 root root 118 2012-02-27 14:45 wfg-0ad-oneiric.list
-rw-r--r-- 1 root root 118 2012-02-27 14:41 wfg-0ad-oneiric.list.save

```.

However sudo apt-get update still seems extraordinarily slow and after approx 10 minutes looks as follows:
```
Ign http://dl.google.com stable InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://dl.google.com stable Release.gpg [189 B]                          
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://gb.archive.ubuntu.com oneiric InRelease                             
Get:2 http://dl.google.com stable Release [2,544 B]                            
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://gb.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://gb.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://security.ubuntu.com oneiric-security Release.gpg                    
Ign http://dl.google.com stable Release                                        
Hit http://archive.canonical.com oneiric Release                               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://gb.archive.ubuntu.com oneiric Release.gpg                           
Ign http://dl.google.com stable/non-free amd64 Packages/DiffIndex              
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://packages.medibuntu.org oneiric InRelease                            
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://gb.archive.ubuntu.com oneiric-updates Release.gpg                   
Hit http://gb.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://archive.canonical.com oneiric/partner Sources                       
Ign http://dl.google.com stable/non-free i386 Packages/DiffIndex               
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://gb.archive.ubuntu.com oneiric Release                               
Ign http://dl.google.com stable/non-free TranslationIndex                      
Hit http://gb.archive.ubuntu.com oneiric-updates Release                       
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://security.ubuntu.com oneiric-security/restricted Sources             
Get:3 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]   
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://gb.archive.ubuntu.com oneiric-backports Release                     
Hit http://packages.medibuntu.org oneiric/free amd64 Packages                  
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ppa.launchpad.net oneiric Release                                   
Get:4 http://dl.google.com stable/non-free amd64 Packages [1,025 B]            
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release                                   
Get:5 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]               
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Get:6 http://dl.google.com stable/non-free i386 Packages [1,010 B]             
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org oneiric/non-free amd64 Packages              
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://packages.medibuntu.org oneiric/free i386 Packages                   
Hit http://packages.medibuntu.org oneiric/non-free i386 Packages               
Ign http://packages.medibuntu.org oneiric/free TranslationIndex                
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://packages.medibuntu.org oneiric/non-free TranslationIndex            
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://dl.google.com stable/non-free Translation-en_GB                     
Ign http://dl.google.com stable/non-free Translation-en                        
Ign http://packages.medibuntu.org oneiric/free Translation-en_GB             
Ign http://packages.medibuntu.org oneiric/free Translation-en                  
Ign http://packages.medibuntu.org oneiric/non-free Translation-en_GB           
Ign http://packages.medibuntu.org oneiric/non-free Translation-en              
Get:7 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]               
Get:8 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]   
Get:9 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]               
Get:10 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:11 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:12 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:13 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:14 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:15 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:16 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:17 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:18 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:19 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:20 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:21 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:22 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:23 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:24 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:25 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:26 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:27 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:28 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:29 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:30 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:31 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:32 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:33 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:34 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:35 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:36 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:37 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:38 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:39 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:40 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:41 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:42 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:43 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:44 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:45 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:46 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:47 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:48 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:49 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:50 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:51 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:52 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:53 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:54 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:55 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:56 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:57 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:58 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:59 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:60 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:61 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:62 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:63 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:64 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:65 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:66 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:67 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:68 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:69 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:70 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:71 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:72 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:73 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:74 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:75 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:76 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:77 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:78 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
Get:79 http://security.ubuntu.com oneiric-security/universe Sources [11.4 kB]
Get:80 http://gb.archive.ubuntu.com oneiric/main Sources [877 kB]
0% [80 Sources 0 B/877 kB 0%] [79 Sources 0 B/11.4 kB 0%]
```.

Do you have any other advice? 

Thanks, Matt

---

### Post by plucky on 2012-02-28
Are you is Great Britain?
How fast should your connection be?

> deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) oneiric-security main restricted universe multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted universe multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) oneiric-proposed main restricted universe multiverse 
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

You don't need the source files.

Open Software Sources and disable all but the main Ubuntu repos and then try again.Then add back the other PPA repos and see which one is causing the downloads to slow down.

You can also in Software Sources,find the best download server for your location.

Good Luck

---

### Post by darjeelingtee on 2012-02-28
Hi thanks again plucky for your continued patience.
I have removed all references to deb-src, opened software sources and disabled all but the main Ubuntu Repos. That works fine however as soon as I add the universe or multiverse repos we get stuck again....
Following a recent relocation from the UK to Sweden I have also changed to the fastest server in Estonia.
I tried to run sudo apt-get install build-essential with only the main repos included but this just gets stuck at 0% downloads for ages.

I am rather running out of ideas as this all worked fine up until last Friday.

Thanks, Matt

---

### Post by plucky on 2012-02-28
Is your connection still fast in Firefox? Try Speedtest.net

> I have also changed to the fastest server in Estonia.

Is there no local mirrors in Sweden you could try?

You could try the MAIN Server to see if that makes a difference.

You should enable all the Canonical Maintained Repositories in the first tag of Software Sources.

Good Luck

---

### Post by darjeelingtee on 2012-02-28
Hi Plucky,

Speed test result in Chromium seems fine (57.82 Mb/s download, 44.51 Mb/s upload). I switched all the repos in the first tab on, rechecked for duplication between sources.list and sources.list.d and changed the server to MAIN. There is still no difference. It feels like something is blocking access... I might try another location. Anything else obvious I can try?

Thanks, Matt

---

