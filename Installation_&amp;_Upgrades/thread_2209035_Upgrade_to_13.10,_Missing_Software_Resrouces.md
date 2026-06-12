---
title: "Upgrade to 13.10, Missing Software Resrouces"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by jmarsz on 2014-03-03
I just recently upgraded my system at home from Ubuntu 13.04 to Ubuntu 13.10 using the upgrade option, and everything went pretty smoothly.  After a bit, I noticed that I haven't been getting any alerts for software updates, so I go and look at my software sources, and notice that it doesn't look like any of the 13.10 sources are in there.  What is the best way to get those added so that I can get updated software onto my system?  Thanks in advance!

---

### Post by deadflowr on 2014-03-03
What does your sources.list say?
Post the output of this
```
cat /etc/apt/sources.list
```
Use Code Tags, please.

---

### Post by jmarsz on 2014-03-03
```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy universe
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu saucy-security main restricted
deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
deb http://security.ubuntu.com/ubuntu saucy-security universe
deb-src http://security.ubuntu.com/ubuntu saucy-security universe
deb http://security.ubuntu.com/ubuntu saucy-security multiverse
deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu saucy partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu saucy main
deb-src http://extras.ubuntu.com/ubuntu saucy main

## This software is for the Teamspeak 3 client
# deb http://apt.twprogrammers.com linux main games net


```

---

### Post by ajgreeny on 2014-03-03
You certainly have all the saucy 13.10 repos enabled, so I wonder if the lack of notifications is due to security updates being carried out automatically now with no user input.

You can check by manually running sudo apt-get update to see if a long list showing as needing updating, and also by going to software sources to see what the settings are in that for updates.

---

### Post by deadflowr on 2014-03-03
Your main Ubuntu repos(main,universe,multiverse,partner,extras) are all there.

Did you have third party repos?
(I noticed you have one for teamspeak which has been disabled,
Normally though third party repos are in the folder
/etc/apt/sources.list.d

From using the upgrade method, I think you should be up to date with whatever packages are installed.
On the lone 13.10 I have, it's been a little while since I've had any updates.
(A while being a couple days, maybe a week or so)

Do you get errors when running an
```
sudo apt-get update
```
and if you run
```
sudo apt-get upgrade
```
are there any updates listed?


But from what I can see, your repo listing is fine.

Edit: ninja'd

---

### Post by ibjsb4 on 2014-03-03
Got your update tab set?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Updates_Tab)

---

### Post by jmarsz on 2014-03-03
This is what I get when I run "sudo apt-get update":

```
jmarsz@Loki:~$ sudo apt-get update
[sudo] password for jmarsz: 
Ign http://security.ubuntu.com saucy-security InRelease
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]                                                                         
Ign http://us.archive.ubuntu.com saucy InRelease                                                                                            
Ign http://archive.canonical.com saucy InRelease                                           
Get:2 http://security.ubuntu.com saucy-security Release [49.6 kB]                          
Ign http://ppa.launchpad.net saucy InRelease                                                                               
Ign http://extras.ubuntu.com saucy InRelease                                                                               
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                             
Get:3 http://archive.canonical.com saucy Release.gpg [933 B]                                         
Hit http://ppa.launchpad.net saucy Release.gpg                                                                                        
Get:4 http://extras.ubuntu.com saucy Release.gpg [72 B]                                              
Ign http://us.archive.ubuntu.com saucy-backports InRelease                                                                          
Hit http://archive.canonical.com saucy Release                                                                                      
Get:5 http://us.archive.ubuntu.com saucy Release.gpg [933 B]                                                                
Hit http://ppa.launchpad.net saucy Release                                                                                         
Hit http://extras.ubuntu.com saucy Release                                                            
Ign http://archive.canonical.com saucy Release                                                        
Err http://extras.ubuntu.com saucy Release                                                            
  
Get:6 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]                                  
Err http://security.ubuntu.com saucy-security Release                                                           
  
Ign http://archive.canonical.com saucy/partner amd64 Packages/DiffIndex                        
Hit http://ppa.launchpad.net saucy/main amd64 Packages                
Get:7 http://us.archive.ubuntu.com saucy-backports Release.gpg [933 B]
Ign http://archive.canonical.com saucy/partner i386 Packages/DiffIndex           
Hit http://us.archive.ubuntu.com saucy Release  
Hit http://ppa.launchpad.net saucy/main i386 Packages                  
Ign http://us.archive.ubuntu.com saucy Release                         
Get:8 http://us.archive.ubuntu.com saucy-updates Release [49.6 kB]     
Hit http://archive.canonical.com saucy/partner amd64 Packages             
Err http://us.archive.ubuntu.com saucy-updates Release                    
  
Hit http://archive.canonical.com saucy/partner i386 Packages             
Hit http://us.archive.ubuntu.com saucy-backports Release              
Ign http://us.archive.ubuntu.com saucy-backports Release                                     
Ign http://us.archive.ubuntu.com saucy/main Sources/DiffIndex                                
Ign http://us.archive.ubuntu.com saucy/restricted Sources/DiffIndex   
Ign http://us.archive.ubuntu.com saucy/universe Sources/DiffIndex                                                                            
Ign http://us.archive.ubuntu.com saucy/multiverse Sources/DiffIndex                                                                          
Ign http://us.archive.ubuntu.com saucy/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/restricted amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net saucy/main Translation-en_US
Ign http://us.archive.ubuntu.com saucy/universe amd64 Packages/DiffIndex
Ign http://ppa.launchpad.net saucy/main Translation-en
Ign http://archive.canonical.com saucy/partner Translation-en_US
Ign http://us.archive.ubuntu.com saucy/multiverse amd64 Packages/DiffIndex
Ign http://archive.canonical.com saucy/partner Translation-en
Ign http://us.archive.ubuntu.com saucy/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy/multiverse i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com saucy/main Translation-en
Hit http://us.archive.ubuntu.com saucy/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy/universe Translation-en
Ign http://us.archive.ubuntu.com saucy-backports/main Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/universe Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Sources/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/main amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/universe amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/multiverse amd64 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/main i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/universe i386 Packages/DiffIndex
Ign http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages/DiffIndex
Hit http://us.archive.ubuntu.com saucy-backports/main Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com saucy-backports/universe Translation-en
Hit http://us.archive.ubuntu.com saucy/main Sources
Hit http://us.archive.ubuntu.com saucy/restricted Sources
Hit http://us.archive.ubuntu.com saucy/universe Sources                                                                                     
Hit http://us.archive.ubuntu.com saucy/multiverse Sources                                                                                   
Hit http://us.archive.ubuntu.com saucy/main amd64 Packages                                                                                  
Hit http://us.archive.ubuntu.com saucy/restricted amd64 Packages                                                                            
Hit http://us.archive.ubuntu.com saucy/universe amd64 Packages                                                                              
Hit http://us.archive.ubuntu.com saucy/multiverse amd64 Packages                                                                            
Hit http://us.archive.ubuntu.com saucy/main i386 Packages                                                                                   
Hit http://us.archive.ubuntu.com saucy/restricted i386 Packages                                                                             
Hit http://us.archive.ubuntu.com saucy/universe i386 Packages                                                                               
Hit http://us.archive.ubuntu.com saucy/multiverse i386 Packages                                                                             
Hit http://us.archive.ubuntu.com saucy-backports/main Sources                                                                               
Hit http://us.archive.ubuntu.com saucy-backports/restricted Sources                                                                         
Hit http://us.archive.ubuntu.com saucy-backports/universe Sources                                                                           
Hit http://us.archive.ubuntu.com saucy-backports/multiverse Sources                                                                         
Hit http://us.archive.ubuntu.com saucy-backports/main amd64 Packages                                                                        
Hit http://us.archive.ubuntu.com saucy-backports/restricted amd64 Packages                                                                  
Hit http://us.archive.ubuntu.com saucy-backports/universe amd64 Packages                                                                    
Hit http://us.archive.ubuntu.com saucy-backports/multiverse amd64 Packages                                                                  
Hit http://us.archive.ubuntu.com saucy-backports/main i386 Packages                                                                         
Hit http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages                                                                   
Hit http://us.archive.ubuntu.com saucy-backports/universe i386 Packages                                                                     
Hit http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages                                                                   
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US                                                                               
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US                                                                           
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US                                                                     
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US                                                               
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Fetched 104 kB in 12s (8,268 B/s)
Reading package lists... Done
W: GPG error: http://archive.canonical.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com saucy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: GPG error: http://us.archive.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://us.archive.ubuntu.com saucy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32

W: GPG error: http://us.archive.ubuntu.com saucy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/saucy-security/Release  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/saucy/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by frank18 on 2014-03-03
> **jmarsz said:**
> I just recently upgraded my system at home from Ubuntu 13.04 to Ubuntu 13.10 using the upgrade option, and everything went pretty smoothly.  After a bit, I noticed that I haven't been getting any alerts for software updates, so I go and look at my software sources, and notice that it doesn't look like any of the 13.10 sources are in there.  What is the best way to get those added so that I can get updated software onto my system?  Thanks in advance!

If i were you i would upgrade to 14.04, i did upgrade from 13.10 and it it solved a few issues and now it's  14.04LTS

---

### Post by ibjsb4 on 2014-03-03
> **frank18 said:**
> If i were you i would upgrade to 14.04, i did upgrade from 13.10 and it it solved a few issues and now it's  14.04LTS

14.04??  Not even out yet.  It worked for you, but your not out of the woods yet :) not till the final release.

To clear those GPG errors open a terminal and enter one line at a time:

```
sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update
```

---

### Post by jmarsz on 2014-03-03
I ran those steps mentioned, and here's what I got:

```
root@Loki:~# apt-get clean
root@Loki:~# cd /var/lib/apt
root@Loki:/var/lib/apt# mv lists lists.old
root@Loki:/var/lib/apt# mkdir -p lists/partial
root@Loki:/var/lib/apt# apt-get clean
root@Loki:/var/lib/apt# apt-get update
Ign http://security.ubuntu.com saucy-security InRelease
Ign http://us.archive.ubuntu.com saucy InRelease                                                                     
Get:1 http://security.ubuntu.com saucy-security Release.gpg [933 B]                                                  
Ign http://us.archive.ubuntu.com saucy-updates InRelease                                                                    
Ign http://archive.canonical.com saucy InRelease                                           
Ign http://extras.ubuntu.com saucy InRelease                                               
Ign http://ppa.launchpad.net saucy InRelease                                               
Ign http://us.archive.ubuntu.com saucy-backports InRelease                                 
Get:2 http://security.ubuntu.com saucy-security Release [49.6 kB]                          
Get:3 http://us.archive.ubuntu.com saucy Release.gpg [933 B]                                                             
Get:4 http://extras.ubuntu.com saucy Release.gpg [72 B]                                                                               
Get:5 http://archive.canonical.com saucy Release.gpg [933 B]                                                                        
Get:6 http://ppa.launchpad.net saucy Release.gpg [316 B]                                                                              
Get:7 http://us.archive.ubuntu.com saucy-updates Release.gpg [933 B]                                                                  
Get:8 http://extras.ubuntu.com saucy Release [9,753 B]                                                                                
Get:9 http://archive.canonical.com saucy Release [7,072 B]                                                                           
Ign http://extras.ubuntu.com saucy Release                                                                                              
Get:10 http://ppa.launchpad.net saucy Release [11.9 kB]                                                                                 
Ign http://archive.canonical.com saucy Release                                                                                              
Get:11 http://extras.ubuntu.com saucy/main Sources [14 B]                                                                     
Get:12 http://ppa.launchpad.net saucy/main amd64 Packages [5,673 B]                                                              
Get:13 http://us.archive.ubuntu.com saucy-backports Release.gpg [933 B]                                                                     
Get:14 http://archive.canonical.com saucy/partner amd64 Packages [2,186 B]                                                             
Ign http://security.ubuntu.com saucy-security Release                                                                                       
Get:15 http://us.archive.ubuntu.com saucy Release [49.6 kB]                                                          
Get:16 http://extras.ubuntu.com saucy/main amd64 Packages [14 B]                                                           
Get:17 http://ppa.launchpad.net saucy/main i386 Packages [5,686 B]                                                                          
Get:18 http://security.ubuntu.com saucy-security/main Sources [33.1 kB]                                                                     
Get:19 http://archive.canonical.com saucy/partner i386 Packages [2,637 B]                                                            
Get:20 http://extras.ubuntu.com saucy/main i386 Packages [14 B]                                                                             
Ign http://us.archive.ubuntu.com saucy Release                                                                                              
Get:21 http://security.ubuntu.com saucy-security/restricted Sources [14 B]                                                                  
Get:22 http://us.archive.ubuntu.com saucy-updates Release [49.6 kB]                                                                      
Get:23 http://security.ubuntu.com saucy-security/universe Sources [8,413 B]                                                
Ign http://ppa.launchpad.net saucy/main Translation-en_US                                                                             
Ign http://archive.canonical.com saucy/partner Translation-en_US                                                                      
Ign http://extras.ubuntu.com saucy/main Translation-en_US                                                                                   
Ign http://ppa.launchpad.net saucy/main Translation-en                                                                      
Get:24 http://security.ubuntu.com saucy-security/multiverse Sources [689 B]                           
Ign http://archive.canonical.com saucy/partner Translation-en                                                                
Ign http://extras.ubuntu.com saucy/main Translation-en                                                
Get:25 http://security.ubuntu.com saucy-security/main amd64 Packages [93.9 kB]  
Ign http://us.archive.ubuntu.com saucy-updates Release                               
Get:26 http://us.archive.ubuntu.com saucy-backports Release [49.6 kB]                
Ign http://us.archive.ubuntu.com saucy-backports Release                             
Get:27 http://us.archive.ubuntu.com saucy/main Sources [1,009 kB]                    
Get:28 http://security.ubuntu.com saucy-security/restricted amd64 Packages [14 B] 
Get:29 http://security.ubuntu.com saucy-security/universe amd64 Packages [33.4 kB]
Get:30 http://security.ubuntu.com saucy-security/multiverse amd64 Packages [1,149 B]                                                        
Get:31 http://security.ubuntu.com saucy-security/main i386 Packages [93.5 kB]                                                               
Get:32 http://security.ubuntu.com saucy-security/restricted i386 Packages [14 B]                                                            
Get:33 http://security.ubuntu.com saucy-security/universe i386 Packages [33.7 kB]                                                           
Get:34 http://security.ubuntu.com saucy-security/multiverse i386 Packages [1,388 B]                                                         
Get:35 http://security.ubuntu.com saucy-security/main Translation-en [51.1 kB]                                                              
Get:36 http://security.ubuntu.com saucy-security/multiverse Translation-en [587 B]                                                          
Get:37 http://security.ubuntu.com saucy-security/restricted Translation-en [14 B]                                                           
Get:38 http://security.ubuntu.com saucy-security/universe Translation-en [19.9 kB]                                                          
Ign http://security.ubuntu.com saucy-security/main Translation-en_US                                                                        
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US                                                                  
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US                                                                  
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US                                                                    
Get:39 http://us.archive.ubuntu.com saucy/restricted Sources [4,759 B]                                                                      
Get:40 http://us.archive.ubuntu.com saucy/universe Sources [6,108 kB]                                                                       
Get:41 http://us.archive.ubuntu.com saucy/multiverse Sources [175 kB]                                                                       
Get:42 http://us.archive.ubuntu.com saucy/main amd64 Packages [1,239 kB]                                                                    
Get:43 http://us.archive.ubuntu.com saucy/restricted amd64 Packages [9,348 B]                                                               
Get:44 http://us.archive.ubuntu.com saucy/universe amd64 Packages [5,643 kB]                                                                
Get:45 http://us.archive.ubuntu.com saucy/multiverse amd64 Packages [131 kB]                                                                
Get:46 http://us.archive.ubuntu.com saucy/main i386 Packages [1,238 kB]                                                                     
Get:47 http://us.archive.ubuntu.com saucy/restricted i386 Packages [9,688 B]                                                                
Get:48 http://us.archive.ubuntu.com saucy/universe i386 Packages [5,652 kB]                                                                 
Get:49 http://us.archive.ubuntu.com saucy/multiverse i386 Packages [133 kB]                                                                 
Get:50 http://us.archive.ubuntu.com saucy/main Translation-en [711 kB]                                                                      
Get:51 http://us.archive.ubuntu.com saucy/multiverse Translation-en [101 kB]                                                                
Get:52 http://us.archive.ubuntu.com saucy/restricted Translation-en [2,686 B]                                                               
Get:53 http://us.archive.ubuntu.com saucy/universe Translation-en [3,886 kB]                                                                
Get:54 http://us.archive.ubuntu.com saucy-updates/main Sources [74.2 kB]                                                                    
Get:55 http://us.archive.ubuntu.com saucy-updates/restricted Sources [14 B]                                                                 
Get:56 http://us.archive.ubuntu.com saucy-updates/universe Sources [67.9 kB]                                                                
Get:57 http://us.archive.ubuntu.com saucy-updates/multiverse Sources [1,358 B]                                                              
Get:58 http://us.archive.ubuntu.com saucy-updates/main amd64 Packages [210 kB]                                                              
Get:59 http://us.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]                                                          
Get:60 http://us.archive.ubuntu.com saucy-updates/universe amd64 Packages [155 kB]                                                          
Get:61 http://us.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1,572 B]                                                       
Get:62 http://us.archive.ubuntu.com saucy-updates/main i386 Packages [209 kB]                                                               
Get:63 http://us.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]                                                           
Get:64 http://us.archive.ubuntu.com saucy-updates/universe i386 Packages [156 kB]                                                           
Get:65 http://us.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1,763 B]                                                        
Get:66 http://us.archive.ubuntu.com saucy-updates/main Translation-en [98.0 kB]                                                             
Get:67 http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en [717 B]                                                         
Get:68 http://us.archive.ubuntu.com saucy-updates/restricted Translation-en [14 B]                                                          
Get:69 http://us.archive.ubuntu.com saucy-updates/universe Translation-en [78.7 kB]                                                         
Get:70 http://us.archive.ubuntu.com saucy-backports/main Sources [14 B]                                                                     
Get:71 http://us.archive.ubuntu.com saucy-backports/restricted Sources [14 B]                                                               
Get:72 http://us.archive.ubuntu.com saucy-backports/universe Sources [2,706 B]                                                              
Get:73 http://us.archive.ubuntu.com saucy-backports/multiverse Sources [834 B]                                                              
Get:74 http://us.archive.ubuntu.com saucy-backports/main amd64 Packages [14 B]                                                              
Get:75 http://us.archive.ubuntu.com saucy-backports/restricted amd64 Packages [14 B]                                                        
Get:76 http://us.archive.ubuntu.com saucy-backports/universe amd64 Packages [2,946 B]                                                       
Get:77 http://us.archive.ubuntu.com saucy-backports/multiverse amd64 Packages [14 B]                                                        
Get:78 http://us.archive.ubuntu.com saucy-backports/main i386 Packages [14 B]                                                               
Get:79 http://us.archive.ubuntu.com saucy-backports/restricted i386 Packages [14 B]                                                         
Get:80 http://us.archive.ubuntu.com saucy-backports/universe i386 Packages [2,935 B]                                                        
Get:81 http://us.archive.ubuntu.com saucy-backports/multiverse i386 Packages [709 B]                                                        
Get:82 http://us.archive.ubuntu.com saucy-backports/main Translation-en [14 B]                                                              
Get:83 http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en [525 B]                                                       
Get:84 http://us.archive.ubuntu.com saucy-backports/restricted Translation-en [14 B]                                                        
Get:85 http://us.archive.ubuntu.com saucy-backports/universe Translation-en [2,864 B]                                                       
Ign http://us.archive.ubuntu.com saucy/main Translation-en_US                                                                               
Ign http://us.archive.ubuntu.com saucy/multiverse Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com saucy/restricted Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com saucy/universe Translation-en_US                                                                           
Ign http://us.archive.ubuntu.com saucy-updates/main Translation-en_US                                                                       
Ign http://us.archive.ubuntu.com saucy-updates/multiverse Translation-en_US                                                                 
Ign http://us.archive.ubuntu.com saucy-updates/restricted Translation-en_US                                                                 
Ign http://us.archive.ubuntu.com saucy-updates/universe Translation-en_US                                                                   
Ign http://us.archive.ubuntu.com saucy-backports/main Translation-en_US                                                                     
Ign http://us.archive.ubuntu.com saucy-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com saucy-backports/universe Translation-en_US
Fetched 27.7 MB in 1min 50s (251 kB/s)
Reading package lists... Done
W: GPG error: http://extras.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://security.ubuntu.com saucy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com saucy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com saucy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://us.archive.ubuntu.com saucy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

---

### Post by jmarsz on 2014-03-03
I think I fixed it!  After seeing those GPG errors, I did a quick Google search (Google is the best!!), and came upon this article:

[http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys](http://askubuntu.com/questions/127326/how-to-fix-missing-gpg-keys)

And once I added the keys back in, I got no errors running apt-get update.

Thanks for everyone's help!

---

### Post by ibjsb4 on 2014-03-03
Nice fix :)  If all is good ..

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

