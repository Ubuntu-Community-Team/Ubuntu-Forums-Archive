---
title: "install restricted-extras"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by jon zendatta on 2010-08-09
trying to install ubuntu-restricted-extras and get this message
[HTML]Package ubuntu-restricted-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-restricted-extras has no installation candidate
[/HTML]
here is my etc/apt/sources.list
```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.ihug.co.nz/ubuntu/ lucid main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid multiverse
deb http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.ihug.co.nz/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security main restricted
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security universe
deb http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid-security multiverse


deb http://packages.medibuntu.org/ lucid free non-free
deb-src http://packages.medibuntu.org/ lucid free non-free
deb http://mirror.ihug.co.nz/ubuntu/ lucid restricted
deb-src http://mirror.ihug.co.nz/ubuntu/ lucid restricted

# Google software repository
# deb http://dl.google.com/linux/deb/ stable non-free
```

cheers for any help, got go out for an hour:KS

---

### Post by pricetech on 2010-08-09
How exactly are you trying to install ??  Are you using Synaptic, Software Center, or what ??

---

### Post by Spice Weasel on 2010-08-09
From the sounds of it, he's installing via apt-get. 

My only suggestion is to add this to your sources.list:

```

deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse

```

---

### Post by jon zendatta on 2010-08-09
ok spice weasel i added those two lines to source.list & get the following

```
sudo apt-get update
Hit http://archive.canonical.com lucid Release.gpg
Get:1 http://packages.medibuntu.org lucid Release.gpg [197B]                   
Get:2 http://archive.ubuntu.com lucid Release.gpg [189B]                       
Ign http://packages.medibuntu.org/ lucid/free Translation-en_NZ                
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_NZ       
Hit http://archive.canonical.com lucid Release                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_NZ             
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_NZ            
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_NZ       
Get:3 http://packages.medibuntu.org lucid Release [6,854B]                     
Ign http://packages.medibuntu.org lucid Release                                
Hit http://packages.medibuntu.org lucid/free Packages                          
Get:4 http://archive.canonical.com lucid/partner Packages [10.9kB]   
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Hit http://packages.medibuntu.org lucid/free Sources                           
Hit http://packages.medibuntu.org lucid/non-free Sources                       
Hit http://archive.canonical.com lucid/partner Sources                         
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_NZ
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_NZ
Get:5 http://archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_NZ
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_NZ
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_NZ
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_NZ
Err http://mirror.ihug.co.nz lucid Release.gpg                                 
  Connection failed
Get:6 http://archive.ubuntu.com lucid Release [57.2kB]                       
Get:7 http://archive.ubuntu.com lucid-updates Release [44.7kB]
Get:8 http://archive.ubuntu.com lucid/main Packages [1,386kB]                  
Err http://mirror.ihug.co.nz/ubuntu/ lucid/main Translation-en_NZ              
  Connection failed
Get:9 http://archive.ubuntu.com lucid/restricted Packages [6,208B]             
Get:10 http://archive.ubuntu.com lucid/universe Packages [5,448kB]             
Err http://mirror.ihug.co.nz/ubuntu/ lucid/restricted Translation-en_NZ        
  Connection failed
Err http://mirror.ihug.co.nz/ubuntu/ lucid/universe Translation-en_NZ          
  Connection failed
Get:11 http://archive.ubuntu.com lucid/multiverse Packages [180kB]             
Get:12 http://archive.ubuntu.com lucid-updates/main Packages [273kB]           
Get:13 http://archive.ubuntu.com lucid-updates/restricted Packages [3,252B]    
Get:14 http://archive.ubuntu.com lucid-updates/universe Packages [89.0kB]      
Get:15 http://archive.ubuntu.com lucid-updates/multiverse Packages [3,771B]    
Err http://mirror.ihug.co.nz/ubuntu/ lucid/multiverse Translation-en_NZ        
  Connection failed
Err http://mirror.ihug.co.nz lucid-updates Release.gpg                         
  Connection failed
Err http://mirror.ihug.co.nz/ubuntu/ lucid-updates/main Translation-en_NZ
  Connection failed
99% [Waiting for headers]  
```                            
 I'm attemting to install restricted extras from the terminal
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Spice Weasel on 2010-08-09
Those are just your other sources failing to connect  to their server, which is what I thought was happening. You're using a mirror site, and APT can't connect to the mirror.

It looks like the official Ubuntu repositories got updated fine, is the output still the same when you enter the install command?

---

### Post by jon zendatta on 2010-08-09
cheers Spice Weasel. Managed to install ok :KS

---

