---
title: "Error authenticating some packages"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by themyth17 on 2011-06-15
when i'm trying to update my system (Ubuntu 10.04) i got this message: 
```
Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages:
apache2
apache2-mpm-prefork
apache2.2-bin
apache2.2-common
isc-dhcp-common
libapache2-mod-php5
libapache2-svn
libapr1
libavahi-core7
libisc62
libisccc60
libmysqlclient16
libwbclient0
libxml2
libxml2-utils
linux-libc-dev
mysql-common
mysql-server-core-5.1
php5-common
php5-curl
php5-mcrypt
php5-mysql
php5-suhosin
postfix
python-libxml2
```

and my /etc/apt/sources.list now is:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb http://eg.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://eg.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid universe
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://eg.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://eg.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://eg.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://eg.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

# deb http://wine.sourceforge.net/apt binary/ # disabled on upgrade to lucid

deb http://http.us.debian.org/debian stable all
deb http://security.debian.org/ stable/updates main contrib
deb http://packages.dotdeb.org/ stable all

```

any help please???

---

### Post by oldos2er on 2011-06-15
Can you run ```
sudo apt-get update
``` and post all the output from that command here?

---

### Post by themyth17 on 2011-06-22
Thanks for your reply, here's all the output i got from ```
sudo apt-get update
```is :
```
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ karmic/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://eg.archive.ubuntu.com lucid Release.gpg                             
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:3 http://eg.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://eg.archive.ubuntu.com karmic Release.gpg                            
Get:4 http://deb.opera.com stable Release.gpg [189B]                           
Ign http://deb.opera.com/opera/ stable/non-free Translation-en_US              
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com/ubuntu/ karmic-security/main Translation-en_US  
Ign http://security.ubuntu.com/ubuntu/ karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ karmic-security/multiverse Translation-en_US
Get:5 http://security.ubuntu.com lucid-security Release [44.7kB]               
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/main Translation-en_US         
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/restricted Translation-en_US   
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/universe Translation-en_US     
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/multiverse Translation-en_US   
Hit http://eg.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/main Translation-en_US 
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/universe Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/multiverse Translation-en_US
Get:6 http://deb.opera.com stable Release [633B]                               
Err http://deb.opera.com stable Release                                        
  
Hit http://eg.archive.ubuntu.com lucid Release                                 
Get:7 http://eg.archive.ubuntu.com lucid-updates Release [44.7kB]              
Get:8 http://dl.google.com stable Release.gpg [198B]                           
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Hit http://eg.archive.ubuntu.com karmic Release                                
Hit http://eg.archive.ubuntu.com karmic-updates Release                        
Get:9 http://security.ubuntu.com lucid-security/main Packages [198kB]          
Get:10 http://dl.google.com stable Release [1,351B]                            
Hit http://eg.archive.ubuntu.com lucid/main Packages                           
Hit http://eg.archive.ubuntu.com lucid/restricted Packages                     
Hit http://eg.archive.ubuntu.com lucid/main Sources                            
Hit http://eg.archive.ubuntu.com lucid/restricted Sources                      
Hit http://eg.archive.ubuntu.com lucid/universe Packages                       
Hit http://eg.archive.ubuntu.com lucid/universe Sources                        
Hit http://eg.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://eg.archive.ubuntu.com lucid/multiverse Sources                      
Get:11 http://dl.google.com stable Release [1,347B]                            
Get:12 http://http.us.debian.org stable Release.gpg [1,671B]                   
Get:13 http://eg.archive.ubuntu.com lucid-updates/main Packages [505kB]        
Get:14 http://packages.dotdeb.org stable Release.gpg [836B]                    
Ign http://packages.dotdeb.org/ stable/all Translation-en_US                   
Get:15 http://security.debian.org stable/updates Release.gpg [836B]            
Ign http://security.debian.org/ stable/updates/main Translation-en_US          
Ign http://security.debian.org/ stable/updates/contrib Translation-en_US       
Ign http://http.us.debian.org/debian/ stable/all Translation-en_US             
Get:16 http://dl.google.com stable/main Packages [1,246B]                      
Get:17 http://packages.dotdeb.org stable Release [2,197B]                      
Ign http://packages.dotdeb.org stable Release                                  
Get:18 http://security.debian.org stable/updates Release [38.4kB]              
Ign http://security.debian.org stable/updates Release                          
Hit http://packages.dotdeb.org stable/all Packages                             
Get:19 http://http.us.debian.org stable Release [79.8kB]                       
Ign http://http.us.debian.org stable Release                                   
Hit http://security.debian.org stable/updates/main Packages                    
Hit http://security.debian.org stable/updates/contrib Packages                 
Ign http://http.us.debian.org stable/all Packages                              
Get:20 http://dl.google.com stable/main Packages [766B]                        
Get:21 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:22 http://security.ubuntu.com lucid-security/main Sources [59.2kB]         
Ign http://http.us.debian.org stable/all Packages                              
Get:23 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:24 http://security.ubuntu.com lucid-security/universe Packages [73.9kB]    
Err http://http.us.debian.org stable/all Packages                              
  404  Not Found [IP: 64.50.233.100 80]
Get:25 http://security.ubuntu.com lucid-security/universe Sources [23.1kB]     
Get:26 http://security.ubuntu.com lucid-security/multiverse Packages [4,561B]  
Get:27 http://security.ubuntu.com lucid-security/multiverse Sources [1,754B]   
Hit http://security.ubuntu.com karmic-security/main Packages      
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources      
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources             
Get:28 http://eg.archive.ubuntu.com lucid-updates/restricted Packages [3,240B]
Get:29 http://eg.archive.ubuntu.com lucid-updates/main Sources [196kB]
Get:30 http://eg.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]
Get:31 http://eg.archive.ubuntu.com lucid-updates/universe Packages [208kB]
Get:32 http://eg.archive.ubuntu.com lucid-updates/universe Sources [76.5kB]
Get:33 http://eg.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]
Get:34 http://eg.archive.ubuntu.com lucid-updates/multiverse Sources [5,053B]
Hit http://eg.archive.ubuntu.com karmic/main Packages
Hit http://eg.archive.ubuntu.com karmic/restricted Packages
Hit http://eg.archive.ubuntu.com karmic/main Sources
Hit http://eg.archive.ubuntu.com karmic/restricted Sources
Hit http://eg.archive.ubuntu.com karmic/universe Packages
Hit http://eg.archive.ubuntu.com karmic/universe Sources
Hit http://eg.archive.ubuntu.com karmic/multiverse Packages
Hit http://eg.archive.ubuntu.com karmic/multiverse Sources
Hit http://eg.archive.ubuntu.com karmic-updates/main Packages
Hit http://eg.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://eg.archive.ubuntu.com karmic-updates/main Sources
Hit http://eg.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://eg.archive.ubuntu.com karmic-updates/universe Packages
Hit http://eg.archive.ubuntu.com karmic-updates/universe Sources
Hit http://eg.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://eg.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 1,464kB in 5s (263kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: GPG error: http://packages.dotdeb.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E9C74FEEA2098A6E
W: GPG error: http://security.debian.org stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: GPG error: http://http.us.debian.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  

W: Failed to fetch http://http.us.debian.org/debian/dists/stable/all/binary-i386/Packages.gz  404  Not Found [IP: 64.50.233.100 80]

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

i still need help...

---

### Post by dino99 on 2011-06-22
open synaptic repo tab and select "main server" instead of yours (eg) then update again

note: you are checking the cdrom: disable it in sources.list (synaptic repo tab)

---

### Post by themyth17 on 2011-06-22
Thanks, but i did so and i got that:

```
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ karmic-security/main Translation-en_US  
Ign http://security.ubuntu.com/ubuntu/ karmic-security/restricted Translation-en_US
Hit http://eg.archive.ubuntu.com karmic Release.gpg                            
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/main Translation-en_US         
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/restricted Translation-en_US   
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Ign http://security.ubuntu.com/ubuntu/ karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ karmic-security/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/universe Translation-en_US     
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic/multiverse Translation-en_US   
Hit http://eg.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/main Translation-en_US 
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/universe Translation-en_US
Hit http://security.ubuntu.com karmic-security Release                         
Ign http://eg.archive.ubuntu.com/ubuntu/ karmic-updates/multiverse Translation-en_US
Hit http://eg.archive.ubuntu.com karmic Release                                
Get:1 http://packages.dotdeb.org stable Release.gpg [836B]                     
Ign http://packages.dotdeb.org/ stable/all Translation-en_US                   
Get:2 http://dl.google.com stable Release.gpg [198B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:3 http://http.us.debian.org stable Release.gpg [1,671B]                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg                       
Hit http://eg.archive.ubuntu.com karmic-updates Release                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US    
Hit http://security.ubuntu.com karmic-security/main Packages                   
Get:4 http://packages.dotdeb.org stable Release [2,197B]                       
Ign http://packages.dotdeb.org stable Release                                  
Hit http://eg.archive.ubuntu.com karmic/main Packages                          
Hit http://eg.archive.ubuntu.com karmic/restricted Packages                    
Hit http://eg.archive.ubuntu.com karmic/main Sources                           
Hit http://eg.archive.ubuntu.com karmic/restricted Sources                     
Hit http://eg.archive.ubuntu.com karmic/universe Packages                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                                    
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources                    
Hit http://security.ubuntu.com karmic-security/restricted Sources              
Hit http://security.ubuntu.com karmic-security/universe Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Ign http://http.us.debian.org/debian/ stable/all Translation-en_US             
Hit http://eg.archive.ubuntu.com karmic/universe Sources                       
Hit http://eg.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://eg.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://packages.dotdeb.org stable/all Packages                             
Hit http://eg.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://eg.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://eg.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://eg.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://eg.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://archive.ubuntu.com lucid-security Release                           
Hit http://eg.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://eg.archive.ubuntu.com karmic-updates/multiverse Packages            
Get:5 http://http.us.debian.org stable Release [79.8kB]                        
Ign http://http.us.debian.org stable Release                                   
Hit http://archive.ubuntu.com lucid/main Packages                              
Hit http://archive.ubuntu.com lucid/restricted Packages                        
Hit http://archive.ubuntu.com lucid/main Sources                               
Hit http://archive.ubuntu.com lucid/restricted Sources                         
Hit http://archive.ubuntu.com lucid/universe Packages                          
Hit http://eg.archive.ubuntu.com karmic-updates/multiverse Sources             
Hit http://archive.ubuntu.com lucid/universe Sources                           
Get:6 http://security.debian.org stable/updates Release.gpg [836B]             
Ign http://security.debian.org/ stable/updates/main Translation-en_US          
Ign http://security.debian.org/ stable/updates/contrib Translation-en_US
Hit http://archive.ubuntu.com lucid/multiverse Packages              
Hit http://archive.ubuntu.com lucid/multiverse Sources                         
Hit http://archive.ubuntu.com lucid-updates/main Packages                      
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                
Hit http://archive.ubuntu.com lucid-updates/main Sources                       
Hit http://archive.ubuntu.com lucid-updates/restricted Sources                 
Hit http://archive.ubuntu.com lucid-updates/universe Packages                  
Hit http://archive.ubuntu.com lucid-updates/universe Sources                   
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                
Ign http://http.us.debian.org stable/all Packages                              
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources                 
Hit http://archive.ubuntu.com lucid-security/main Packages                     
Hit http://archive.ubuntu.com lucid-security/restricted Packages               
Hit http://archive.ubuntu.com lucid-security/main Sources                      
Hit http://archive.ubuntu.com lucid-security/restricted Sources                
Hit http://archive.ubuntu.com lucid-security/universe Packages                 
Hit http://archive.ubuntu.com lucid-security/universe Sources                  
Hit http://archive.ubuntu.com lucid-security/multiverse Packages               
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                
Ign http://http.us.debian.org stable/all Packages                              
Get:7 http://security.debian.org stable/updates Release [38.4kB]     
Ign http://security.debian.org stable/updates Release                        
Err http://http.us.debian.org stable/all Packages                      
  404  Not Found [IP: 64.50.233.100 80]
Hit http://security.debian.org stable/updates/main Packages
Get:8 http://dl.google.com stable Release.gpg [198B]
Hit http://security.debian.org stable/updates/contrib Packages
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US
Get:9 http://dl.google.com stable Release [1,351B]
Get:10 http://dl.google.com stable Release [1,347B]
Get:11 http://dl.google.com stable/main Packages [1,246B]
Get:12 http://dl.google.com stable/main Packages [766B]
Fetched 8,452B in 4s (1,845B/s)
W: GPG error: http://packages.dotdeb.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E9C74FEEA2098A6E
W: GPG error: http://http.us.debian.org stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: GPG error: http://security.debian.org stable/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA
W: Failed to fetch http://http.us.debian.org/debian/dists/stable/all/binary-i386/Packages.gz  404  Not Found [IP: 64.50.233.100 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

so what i have to do now?

---

### Post by themyth17 on 2011-06-22
I updated the error output in the last reply (#5)..

---

### Post by oldos2er on 2011-06-22
You should remove the lines referring to karmic in your sources.list. Why are you using debian repos?

---

### Post by themyth17 on 2011-06-22
I'm new with this so here is my sources.list : 
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb-src http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe
deb-src http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://eg.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://eg.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb-src http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu lucid-security multiverse

# deb http://wine.sourceforge.net/apt binary/ # disabled on upgrade to lucid

deb http://http.us.debian.org/debian stable all
deb http://security.debian.org/ stable/updates main contrib
deb http://packages.dotdeb.org/ stable all

```

what i got from you is that i have to delete the last 3 lines which contain the debian, i triad that, and i have no errors then but i can't also upgrade!

---

### Post by oldos2er on 2011-06-25
Can you explain what 'can't upgrade' refers to? If you're having errors running sudo apt-get upgrade, please post them here.

---

### Post by themyth17 on 2011-06-26
I had some errors, but i fixed it now, thanks a lot for your help :D

---

