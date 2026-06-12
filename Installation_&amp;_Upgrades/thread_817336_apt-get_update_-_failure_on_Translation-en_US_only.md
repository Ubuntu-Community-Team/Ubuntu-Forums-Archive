---
title: "apt-get update - failure on Translation-en_US only"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by gary vollink on 2008-06-03
root@XUGVOLLMSTP1:/etc/apt# ls -la /etc/apt/sources.list.d
total 8
drwxr-xr-x 2 root root 4096 2008-04-22 10:20 .
drwxr-xr-x 4 root root 4096 2008-07-03 13:13 ..
root@XUGVOLLMSTP1:/etc/apt# cat sources.list

```
# deb cdrom:[Xubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse

```
  
root@XUGVOLLMSTP1:~# apt-get update```

Hit http://archive.canonical.com hardy Release.gpg
Get:1 http://security.ubuntu.com hardy-security Release.gpg [191B]             
Get:2 http://us.archive.ubuntu.com hardy Release.gpg                           
Ign http://archive.canonical.com hardy/partner Translation-en_US               
Ign http://security.ubuntu.com hardy-security/main Translation-en_US           
Err http://us.archive.ubuntu.com hardy Release.gpg                             
  This HTTP server has broken range support
Err http://us.archive.ubuntu.com hardy/main Translation-en_US                  
  Connection failed
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US     
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US            
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US      
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US    
Hit http://security.ubuntu.com hardy-security Release                  
Get:3 http://us.archive.ubuntu.com hardy-updates Release.gpg [191B]
Hit http://security.ubuntu.com hardy-security/main Packages            
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US  
Hit http://security.ubuntu.com hardy-security/restricted Packages      
Hit http://security.ubuntu.com hardy-security/universe Packages        
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Hit http://security.ubuntu.com hardy-security/multiverse Packages      
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US        
Err http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US  
  Error reading from server. Remote end closed connection
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com hardy Release                                 
Get:5 http://us.archive.ubuntu.com hardy-updates Release                       
Get:6 http://us.archive.ubuntu.com hardy-updates Release                       
Hit http://us.archive.ubuntu.com hardy-backports Release                       
Get:7 http://us.archive.ubuntu.com hardy/main Packages      
```

---

