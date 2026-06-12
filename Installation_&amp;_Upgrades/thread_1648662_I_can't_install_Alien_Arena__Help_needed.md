---
title: "I can't install Alien Arena :: Help needed"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by maizuddin35 on 2010-12-19
Hello guys, 

I want to install Alien Arena in my ubuntu 10.10, when insert this into my terminal to install it

```
sudo apt-get build-dep alien-arena
```

this come out

```

adib@maizuddin35:~$ sudo apt-get build-dep alien-arena
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/ppa.launchpad.net_meerkat_stable_ubuntu_dists_maverick_main_source_Sources - open (2: No such file or directory)

```

what is the problem with it? I don't understand that much and don't know how to solve it. 
help needed here, anyone.
thanks in advanced.

---

### Post by sikander3786 on 2010-12-19
Please post the complete output of this command.

```
sudo apt-get update
```

---

### Post by maizuddin35 on 2010-12-19
here it goes :

```
adib@maizuddin35:~$ sudo apt-get update
Hit http://my.archive.ubuntu.com maverick Release.gpg                          
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://my.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://my.archive.ubuntu.com maverick Release                              
Hit http://my.archive.ubuntu.com maverick-updates Release                      
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://my.archive.ubuntu.com maverick/main Sources                         
Hit http://my.archive.ubuntu.com maverick/restricted Sources                   
Hit http://my.archive.ubuntu.com maverick/universe Sources                     
Hit http://my.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://my.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://my.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://my.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://my.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://my.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://my.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://my.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://my.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://my.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://my.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://my.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://my.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Get:1 http://ppa.launchpad.net jaunty Release.gpg [316B]                       
Ign http://ppa.launchpad.net/sunab/ppa/ubuntu/ jaunty/main Translation-en      
Ign http://ppa.launchpad.net/sunab/ppa/ubuntu/ jaunty/main Translation-en_US   
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Get:2 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en_US
Get:3 http://ppa.launchpad.net maverick Release.gpg [307B]                     
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en_US
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/meerkat/stable/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/meerkat/stable/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick/main Sources                             
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://ppa.launchpad.net/midori/ppa/ubuntu/ maverick/main Translation-en   
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://ppa.launchpad.net/midori/ppa/ubuntu/ maverick/main Translation-en_US
Get:7 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/ maverick/main Translation-en_US
Get:8 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/ maverick/main Translation-en_US
Get:9 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/sikon/steadyflow/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sikon/steadyflow/ubuntu/ maverick/main Translation-en_US
Get:10 http://ppa.launchpad.net maverick Release.gpg [316B]                    
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_US
Get:11 http://ppa.launchpad.net maverick Release.gpg [316B]                    
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Get:12 http://ppa.launchpad.net maverick Release.gpg [316B]                    
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Get:13 http://ppa.launchpad.net maverick Release.gpg [316B]                    
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Get:14 http://ppa.launchpad.net maverick Release.gpg [316B]                    
Ign http://ppa.launchpad.net/webkit-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webkit-team/ppa/ubuntu/ maverick/main Translation-en_US
Get:15 http://ppa.launchpad.net jaunty Release [74.7kB]                        
Ign http://ppa.launchpad.net jaunty Release                                    
Get:16 http://ppa.launchpad.net maverick Release [39.8kB]                      
Hit http://archive.canonical.com maverick Release                              
Hit http://archive.canonical.com maverick/partner i386 Packages                
Get:17 http://ppa.launchpad.net maverick Release [57.3kB]                      
Get:18 http://ppa.launchpad.net maverick Release [9,770B]                      
Get:19 http://ppa.launchpad.net maverick Release [39.8kB]                      
Ign http://ppa.launchpad.net maverick Release                                  
Get:20 http://ppa.launchpad.net maverick Release [39.8kB]                      
Get:21 http://ppa.launchpad.net maverick Release [39.8kB]                      
Get:22 http://ppa.launchpad.net maverick Release [9,747B]                      
Get:23 http://ppa.launchpad.net maverick Release [57.3kB]                      
Get:24 http://ppa.launchpad.net maverick Release [9,750B]                      
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Get:25 http://ppa.launchpad.net maverick Release [39.8kB]                      
Ign http://ppa.launchpad.net maverick Release                                  
Get:26 http://ppa.launchpad.net maverick Release [57.3kB]                      
Ign http://ppa.launchpad.net maverick Release                                  
Get:27 http://ppa.launchpad.net maverick Release [9,753B]                      
Get:28 http://ppa.launchpad.net maverick Release [39.8kB]                      
Ign http://ppa.launchpad.net jaunty/main Sources/DiffIndex                     
Ign http://ppa.launchpad.net jaunty/main i386 Packages/DiffIndex           
Ign http://ppa.launchpad.net maverick/main Sources                         
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Get:29 http://ppa.launchpad.net maverick/main Sources [1,414B]          
Get:30 http://ppa.launchpad.net maverick/main i386 Packages [3,621B]           
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://ppa.launchpad.net jaunty/main Sources                        
Hit http://ppa.launchpad.net jaunty/main i386 Packages                  
Ign http://ppa.launchpad.net maverick/main Sources                      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex            
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex      
Ign http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Err http://ppa.launchpad.net maverick/main Sources                      
  404  Not Found
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Hit http://ppa.launchpad.net maverick/main Sources                      
Hit http://ppa.launchpad.net maverick/main i386 Packages                
Err http://ppa.launchpad.net maverick/main i386 Packages                
  404  Not Found
Err http://dl.google.com stable Release.gpg                                    
  Could not connect to dl.google.com:80 (209.85.175.93). - connect (110: Connection timed out) [IP: 209.85.175.93 80]
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]
Err http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US
  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]
Ign http://dl.google.com stable Release          
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Ign http://dl.google.com stable/main i386 Packages
Ign http://dl.google.com stable/main i386 Packages
Err http://dl.google.com stable/main i386 Packages
  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]
Fetched 49.3kB in 1min 24s (585B/s)
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B5115B98AA836CA8
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DEF31B9A9E345C0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F678A01569113AE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E5F6C1A69241F1
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF32D8D5430711DE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 610C90B170C398A2
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 541F93483C97CFDE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E4010F076C2225A4
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 991E6CF92D9A3C5B
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Could not connect to dl.google.com:80 (209.85.175.93). - connect (110: Connection timed out) [IP: 209.85.175.93 80]

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en.bz2  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US.bz2  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]

W: Failed to fetch http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/meerkat/stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz  Unable to connect to dl.google.com:http: [IP: 209.85.175.93 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

its pretty messy with the gpg errors..if you can help with those also, with some tips and something it would be nice.

thanks for the reply btw

---

### Post by sikander3786 on 2010-12-19
You are Welcome :-)

We need to see the output of these commands as well.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by maizuddin35 on 2010-12-19
this one is the first command :

```
cat /etc/apt/sources.list
```

```
adib@maizuddin35:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://my.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://my.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://my.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick universe
deb http://my.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://my.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://my.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://my.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://my.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://my.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
## deb http://www.sourceslist.eu/repo/ubuntu maverick main non-free

## for kdenlive
deb http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main

```

and this one is the second one
```
ls -l /etc/apt/sources.list.d
```

```
adib@maizuddin35:~$ ls -l /etc/apt/sources.list.d
total 128
-rw-r--r-- 1 root root 156 2010-12-19 21:56 and471-kazam-daily-builds-maverick.list
-rw-r--r-- 1 root root 156 2010-12-19 21:56 and471-kazam-daily-builds-maverick.list.save
-rw-r--r-- 1 root root 134 2010-12-19 21:56 bean123ch-burg-maverick.list
-rw-r--r-- 1 root root 134 2010-12-19 21:56 bean123ch-burg-maverick.list.save
-rw-r--r-- 1 root root 170 2010-12-19 21:56 caffeine-developers-caffeine-dev-maverick.list
-rw-r--r-- 1 root root 170 2010-12-19 21:56 caffeine-developers-caffeine-dev-maverick.list.save
-rw-r--r-- 1 root root 140 2010-12-19 21:56 elementaryart-ppa-maverick.list
-rw-r--r-- 1 root root 140 2010-12-19 21:56 elementaryart-ppa-maverick.list.save
-rw-r--r-- 1 root root 176 2010-12-19 21:56 google-chrome.list
-rw-r--r-- 1 root root 176 2010-12-19 21:56 google-chrome.list.save
-rw-r--r-- 1 root root 182 2010-12-18 03:45 google-talkplugin.list.save
-rw-r--r-- 1 root root 134 2010-12-19 21:56 meerkat-stable-maverick.list
-rw-r--r-- 1 root root 134 2010-12-19 21:56 meerkat-stable-maverick.list.save
-rw-r--r-- 1 root root 126 2010-12-19 21:56 midori-ppa-maverick.list
-rw-r--r-- 1 root root 126 2010-12-19 21:56 midori-ppa-maverick.list.save
-rw-r--r-- 1 root root 148 2010-12-19 21:56 nikolay-blohin-histwi-maverick.list
-rw-r--r-- 1 root root 148 2010-12-19 21:56 nikolay-blohin-histwi-maverick.list.save
-rw-r--r-- 1 root root 146 2010-12-19 21:56 nikount-orta-desktop-maverick.list
-rw-r--r-- 1 root root 146 2010-12-19 21:56 nikount-orta-desktop-maverick.list.save
-rw-r--r-- 1 root root 144 2010-12-18 03:45 performous-team-ppa-maverick.list.save
-rw-r--r-- 1 root root 138 2010-12-19 21:56 sikon-steadyflow-maverick.list
-rw-r--r-- 1 root root 138 2010-12-19 21:56 sikon-steadyflow-maverick.list.save
-rw-r--r-- 1 root root 138 2010-12-19 21:56 synapse-core-ppa-maverick.list
-rw-r--r-- 1 root root 138 2010-12-19 21:56 synapse-core-ppa-maverick.list.save
-rw-r--r-- 1 root root 134 2010-12-19 21:56 tiheum-equinox-maverick.list
-rw-r--r-- 1 root root 134 2010-12-19 21:56 tiheum-equinox-maverick.list.save
-rw-r--r-- 1 root root 132 2010-12-19 21:56 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root 132 2010-12-19 21:56 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 2010-12-19 21:56 ubuntu-wine-ppa-maverick.list
-rw-r--r-- 1 root root 136 2010-12-19 21:56 ubuntu-wine-ppa-maverick.list.save
-rw-r--r-- 1 root root 136 2010-12-19 21:56 webkit-team-ppa-maverick.list
-rw-r--r-- 1 root root 136 2010-12-19 21:56 webkit-team-ppa-maverick.list.save
adib@maizuddin35:~$ 

```

---

### Post by sikander3786 on 2010-12-19
Jaunty reached end of life in this October so its repositories might not be responding any longer. Edit your /etc/apt/sources.list by,

```
gksudo gedit /etc/apt/sources.list
```

And comment out these 2 lines in the beginning with a #. They are at the end of your file.

```
deb http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
```

So they look like,

```
#deb http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
#deb-src http://ppa.launchpad.net/sunab/ppa/ubuntu jaunty main
```

Save and close.

Then from Software Center > Edit > Software Sources > Other Software Tab, disable the following ones.

```
meerkat-stable-maverick.list
meerkat-stable-maverick.list.save
google-chrome.list
google-chrome.list.save
google-talkplugin.list.save
```

Once again run apt-get update from the Terminal and post the output.

---

### Post by maizuddin35 on 2010-12-19
ok, getting work on with this thing.

---

### Post by maizuddin35 on 2010-12-19
I have done most of the things you tell me to do, thank so much

here is the update :

```
adib@maizuddin35:~$ sudo apt-get update
Hit http://my.archive.ubuntu.com maverick Release.gpg
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://my.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://my.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://my.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://my.archive.ubuntu.com maverick Release                              
Hit http://my.archive.ubuntu.com maverick-updates Release                      
Hit http://my.archive.ubuntu.com maverick/main Sources                         
Hit http://my.archive.ubuntu.com maverick/restricted Sources                   
Hit http://my.archive.ubuntu.com maverick/universe Sources                     
Hit http://my.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://my.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://my.archive.ubuntu.com maverick/restricted i386 Packages             
Hit http://my.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://my.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://my.archive.ubuntu.com maverick-updates/main Sources                 
Hit http://my.archive.ubuntu.com maverick-updates/restricted Sources           
Hit http://my.archive.ubuntu.com maverick-updates/universe Sources             
Hit http://my.archive.ubuntu.com maverick-updates/multiverse Sources           
Hit http://my.archive.ubuntu.com maverick-updates/main i386 Packages           
Hit http://my.archive.ubuntu.com maverick-updates/restricted i386 Packages     
Hit http://my.archive.ubuntu.com maverick-updates/universe i386 Packages       
Hit http://my.archive.ubuntu.com maverick-updates/multiverse i386 Packages     
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Get:1 http://ppa.launchpad.net maverick Release.gpg [316B]                     
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/ maverick/main Translation-en_US
Hit http://archive.canonical.com maverick Release                              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Get:2 http://ppa.launchpad.net maverick Release.gpg [307B]           
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/bean123ch/burg/ubuntu/ maverick/main Translation-en_US
Get:3 http://ppa.launchpad.net maverick Release.gpg [316B]           
Ign http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/caffeine-developers/caffeine-dev/ubuntu/ maverick/main Translation-en_US
Get:4 http://ppa.launchpad.net maverick Release.gpg [316B]           
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://extras.ubuntu.com maverick/main Sources                   
Ign http://ppa.launchpad.net/elementaryart/ppa/ubuntu/ maverick/main Translation-en_US
Get:5 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/midori/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/midori/ppa/ubuntu/ maverick/main Translation-en_US
Get:6 http://ppa.launchpad.net maverick Release.gpg [316B]           
Ign http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/ maverick/main Translation-en
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://ppa.launchpad.net/nikolay-blohin/histwi/ubuntu/ maverick/main Translation-en_US
Get:7 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Get:8 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/sikon/steadyflow/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/sikon/steadyflow/ubuntu/ maverick/main Translation-en_US
Get:9 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/synapse-core/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Get:10 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tiheum/equinox/ubuntu/ maverick/main Translation-en_US
Get:11 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Get:12 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_US
Get:13 http://ppa.launchpad.net maverick Release.gpg [316B]
Ign http://ppa.launchpad.net/webkit-team/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/webkit-team/ppa/ubuntu/ maverick/main Translation-en_US
Get:14 http://ppa.launchpad.net maverick Release [39.8kB]
Get:15 http://ppa.launchpad.net maverick Release [57.3kB]
Ign http://ppa.launchpad.net maverick Release              
Ign http://ppa.launchpad.net maverick Release              
Get:16 http://ppa.launchpad.net maverick Release [9,770B]
Get:17 http://ppa.launchpad.net maverick Release [39.8kB]
Get:18 http://ppa.launchpad.net maverick Release [39.8kB]
Ign http://ppa.launchpad.net maverick Release              
Ign http://ppa.launchpad.net maverick Release     
Ign http://ppa.launchpad.net maverick Release     
Get:19 http://ppa.launchpad.net maverick Release [39.8kB]
Get:20 http://ppa.launchpad.net maverick Release [9,747B]
Ign http://ppa.launchpad.net maverick Release     
Ign http://ppa.launchpad.net maverick Release     
Get:21 http://ppa.launchpad.net maverick Release [57.3kB]
Ign http://ppa.launchpad.net maverick Release     
Get:22 http://ppa.launchpad.net maverick Release [9,750B]
Get:23 http://ppa.launchpad.net maverick Release [39.8kB]
Get:24 http://ppa.launchpad.net maverick Release [57.3kB]  
Get:25 http://ppa.launchpad.net maverick Release [9,753B]  
Get:26 http://ppa.launchpad.net maverick Release [39.8kB]  
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release
Ign http://ppa.launchpad.net maverick Release     
Ign http://ppa.launchpad.net maverick Release     
Ign http://ppa.launchpad.net maverick Release     
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Ign http://ppa.launchpad.net maverick/main Sources/DiffIndex                   
Ign http://ppa.launchpad.net maverick/main i386 Packages/DiffIndex             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Fetched 4,112B in 9s (418B/s)                                                  
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4DEF31B9A9E345C0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0F678A01569113AE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4D17133CFC5D50C5
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61E5F6C1A69241F1
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CF32D8D5430711DE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 610C90B170C398A2
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 541F93483C97CFDE
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E4010F076C2225A4
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 464AD83D4631BBEA
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 991E6CF92D9A3C5B
```

still got the errors though . What exactly making this error thingy ?
so what happen now, is it ok ?

---

### Post by sikander3786 on 2010-12-19
Try adding the missing gpg keys by,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4DEF31B9A9E345C0
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 55708F1EE06803C5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0F678A01569113AE
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4D17133CFC5D50C5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 61E5F6C1A69241F1
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CF32D8D5430711DE
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 610C90B170C398A2
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 541F93483C97CFDE
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E4010F076C2225A4
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 464AD83D4631BBEA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6AF0E1940624A220
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5A9A06AEF9CB8DB0
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 991E6CF92D9A3C5B

```

Run all these commands one-by-one and try apt-get update once again.

---

### Post by maizuddin35 on 2010-12-19
ok, doing it now, btw , can you tell me how, you actually get the gpg keys and everything?

---

### Post by maizuddin35 on 2010-12-19
Thank you sikander3786 for the help, my problem is solved. just wanted to ask you about that thing, i just asked from the last reply from me.

---

### Post by sikander3786 on 2010-12-19
Glad to know that it is all sorted :-)

GPG keys are a sort of digital signatures to verify the sources.

[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Hope the links above help you understand GPG.

Happy Ubuntu-ing!

---

### Post by maizuddin35 on 2010-12-19
thanks for the help and the information about that. :)

---

