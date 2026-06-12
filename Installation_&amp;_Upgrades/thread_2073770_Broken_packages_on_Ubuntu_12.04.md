---
title: "Broken packages on Ubuntu 12.04"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by GVRV on 2012-10-20
G'Day everyone, 

I've got a few broken packages on my system that I cannot seem to fix. 

Output from dpkg

```
gaurav@gaurav-gamma:~$ sudo dpkg --configure -a
Setting up man-db (2.6.1-2) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up byobu (5.17-0ubuntu1) ...
dpkg: error processing byobu (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 byobu
```

If I try to autoremove them, I get 

```
gaurav@gaurav-gamma:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up man-db (2.6.1-2) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up byobu (5.17-0ubuntu1) ...
dpkg: error processing byobu (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 byobu
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone tell me how I can fix this? I don't want to risk upgrading to 12.10 before I can. Thanks!

---

### Post by grahammechanical on 2012-10-20
Installing 12.10 most likely would fix this problem because 12.10 uses a different set of repositories to 12.10 but that is not the way to fix problems. Is it?

The issue seems to be with byobu. Have you tried re-installing byobu? Why do you have it installed? It is not installed by default on my 12.10 Ubuntu. Which version of Ubuntu are you using?

Regards.

---

### Post by raja.genupula on 2012-10-20
do this 
```
sudo dpkg -r man-db
sudo dpkg -r byobu
sudo apt-get upgrade
sudo apt-get install -f

```

---

### Post by GVRV on 2012-10-20
No, byobu is the problem because I recently tried to install juju using apt-get. The problems started with man-db and flashplugin-installer. I removed flashplugin-installer, and I temporarily removed man-db as well. But now when I try to install man-db it still remains broken. 

The output of the whole process, if it helps. 

```

gaurav@gaurav-gamma:~$ sudo apt-get remove man-db
[sudo] password for gaurav: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  man-db
0 upgraded, 0 newly installed, 1 to remove and 33 not upgraded.
2 not fully installed or removed.
After this operation, 1,790 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 366233 files and directories currently installed.)
Removing man-db ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file...
Setting up byobu (5.17-0ubuntu1) ...
dpkg: error processing byobu (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 byobu
E: Sub-process /usr/bin/dpkg returned an error code (1)
gaurav@gaurav-gamma:~$ sudo apt-get remove byobu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  byobu
0 upgraded, 0 newly installed, 1 to remove and 33 not upgraded.
1 not fully installed or removed.
After this operation, 428 kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 366080 files and directories currently installed.)
Removing byobu ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
gaurav@gaurav-gamma:~$ sudo dpkg --configure -a
gaurav@gaurav-gamma:~$ sudo apt-get install man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  groff
The following NEW packages will be installed:
  man-db
0 upgraded, 1 newly installed, 0 to remove and 33 not upgraded.
Need to get 756 kB of archives.
After this operation, 1,790 kB of additional disk space will be used.
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise/main man-db amd64 2.6.1-2 [756 kB]
Fetched 756 kB in 7s (101 kB/s)                                                
Preconfiguring packages ...
man-db failed to preconfigure, with exit status 1
Selecting previously unselected package man-db.
(Reading database ... 365946 files and directories currently installed.)
Unpacking man-db (from .../man-db_2.6.1-2_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Setting up man-db (2.6.1-2) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by GVRV on 2012-10-20
> **raja.genupula said:**
> do this 
```
sudo dpkg -r man-db
sudo dpkg -r byobu
sudo apt-get upgrade
sudo apt-get install -f

```
Tried doing what you suggested. Got errors when upgrading. 

```

gaurav@gaurav-gamma:~$ sudo dpkg -r man-db
(Reading database ... 366098 files and directories currently installed.)
Removing man-db ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file...
gaurav@gaurav-gamma:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor apport apport-gtk coreutils libc-bin libc-dev-bin libc6 libc6:i386
  libc6-dev libc6-i386 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx
  libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libglu1-mesa
  libglu1-mesa:i386 libparted0debian1 libxatracker1 login multiarch-support
  onboard parted passwd python-apport python-problem-report sessioninstaller
  update-notifier update-notifier-common wpasupplicant x11-utils
  xserver-xorg-video-intel
33 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.9 MB of archives.
After this operation, 76.8 kB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main coreutils amd64 8.13-3ubuntu3.1 [2,216 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main login amd64 1:4.1.4.2+svn3283-3ubuntu5.1 [291 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc-bin amd64 2.15-0ubuntu10.3 [1,181 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.3 [3,993 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc-dev-bin amd64 2.15-0ubuntu10.3 [84.5 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-dev amd64 2.15-0ubuntu10.3 [2,945 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 i386 2.15-0ubuntu10.3 [3,940 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.3 [4,653 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apparmor amd64 2.7.102-0ubuntu3.2 [357 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libparted0debian1 amd64 2.3-8ubuntu5.1 [240 kB]
Get:11 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dri amd64 8.0.4-0ubuntu0.1 [3,056 kB]
Get:12 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dri i386 8.0.4-0ubuntu0.1 [3,098 kB]
Get:13 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-glx i386 8.0.4-0ubuntu0.1 [103 kB]
Get:14 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-glx amd64 8.0.4-0ubuntu0.1 [104 kB]
Get:15 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglapi-mesa amd64 8.0.4-0ubuntu0.1 [21.1 kB]
Get:16 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglapi-mesa i386 8.0.4-0ubuntu0.1 [21.1 kB]
Get:17 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libxatracker1 amd64 8.0.4-0ubuntu0.1 [351 kB]
Get:18 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier amd64 0.119ubuntu8.6 [57.3 kB]
Get:19 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]
Get:20 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglu1-mesa i386 8.0.4-0ubuntu0.1 [165 kB]
Get:21 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglu1-mesa amd64 8.0.4-0ubuntu0.1 [161 kB]
Get:22 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main multiarch-support amd64 2.15-0ubuntu10.3 [4,480 B]
Get:23 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main passwd amd64 1:4.1.4.2+svn3283-3ubuntu5.1 [959 kB]
Get:24 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main parted amd64 2.3-8ubuntu5.1 [52.4 kB]
Get:25 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu14 [9,882 B]
Get:26 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu14 [79.6 kB]
Get:27 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu14 [145 kB]
Get:28 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu14 [9,224 B]
Get:29 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main onboard amd64 0.97.0-0ubuntu4 [406 kB]
Get:30 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main wpasupplicant amd64 0.7.3-6ubuntu2.1 [490 kB]
Get:31 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main x11-utils amd64 7.6+4ubuntu0.1 [230 kB]
Get:32 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-intel amd64 2:2.17.0-1ubuntu4.2 [238 kB]
Get:33 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main sessioninstaller all 0.20+bzr128-0ubuntu1.2 [29.7 kB]
Fetched 29.9 MB in 1min 37s (307 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
apparmor failed to preconfigure, with exit status 1
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace coreutils 8.13-3ubuntu3 (using .../coreutils_8.13-3ubuntu3.1_amd64.deb) ...
Unpacking replacement coreutils ...
Processing triggers for install-info ...
Setting up coreutils (8.13-3ubuntu3.1) ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement login ...
Setting up login (1:4.1.4.2+svn3283-3ubuntu5.1) ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.2 (using .../libc-bin_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc-bin ...
Setting up libc-bin (2.15-0ubuntu10.3) ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6-i386 2.15-0ubuntu10.2 (using .../libc6-i386_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Replaced by files in installed package libc6:i386 ...
Preparing to replace libc-dev-bin 2.15-0ubuntu10.2 (using .../libc-dev-bin_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using .../libc6-dev_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
gaurav@gaurav-gamma:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
3 not fully installed or removed.
Need to get 0 B/8,593 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by raja.genupula on 2012-10-20
Ok do this 

```
sudo rm -rf /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb 
sudo rm -rf  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
```

then > sudo apt-get update
sudo apt-get upgrade

---

### Post by GVRV on 2012-10-20
> **raja.genupula said:**
> Ok do this 

```
sudo rm -rf /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb 
sudo rm -rf  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
```

then
Still ends up where we started. 

```

gaurav@gaurav-gamma:~$ sudo rm -rf /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb 
gaurav@gaurav-gamma:~$ sudo rm -rf /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb 
gaurav@gaurav-gamma:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease                                      
Ign http://in.archive.ubuntu.com precise InRelease                             
Ign http://in.archive.ubuntu.com precise-updates InRelease                     
Ign http://in.archive.ubuntu.com precise-backports InRelease                   
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.ubuntu.com precise InRelease                                
Hit http://dl.google.com stable Release.gpg                                    
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://dl.google.com stable Release                                        
Hit http://in.archive.ubuntu.com precise Release.gpg                           
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://archive.ubuntu.com precise Release.gpg                              
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://security.ubuntu.com precise-security Release                        
Get:1 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://archive.ubuntu.com precise Release                                  
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release.gpg                               
Ign http://dl.google.com stable/main TranslationIndex                          
Get:2 http://in.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://in.archive.ubuntu.com precise Release                               
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise/main Sources                              
Get:3 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:4 http://in.archive.ubuntu.com precise-backports Release [49.6 kB]         
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://dl.google.com stable/main Translation-en_IN                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://in.archive.ubuntu.com precise/restricted Sources                    
Hit http://in.archive.ubuntu.com precise/main Sources
Hit http://in.archive.ubuntu.com precise/multiverse Sources
Hit http://in.archive.ubuntu.com precise/universe Sources                      
Hit http://in.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://in.archive.ubuntu.com precise/main i386 Packages           
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://in.archive.ubuntu.com precise/universe i386 Packages       
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://in.archive.ubuntu.com precise/main TranslationIndex        
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex  
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex    
Get:5 http://in.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:6 http://in.archive.ubuntu.com precise-updates/main Sources [178 kB]       
Get:7 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:8 http://in.archive.ubuntu.com precise-updates/universe Sources [60.2 kB]  
Get:9 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [405 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_IN                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:10 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]
Get:11 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [149 kB]
Ign http://ppa.launchpad.net precise/main Translation-en_IN                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:12 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]
Get:13 http://in.archive.ubuntu.com precise-updates/main i386 Packages [410 kB]
Get:14 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:15 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [149 kB]
Get:16 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:17 http://in.archive.ubuntu.com precise-backports/main Sources [2,422 B]   
Get:18 http://in.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:19 http://in.archive.ubuntu.com precise-backports/universe Sources [15.8 kB]
Get:20 http://in.archive.ubuntu.com precise-backports/multiverse Sources [2,669 B]
Get:21 http://in.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]
Get:22 http://in.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:23 http://in.archive.ubuntu.com precise-backports/universe amd64 Packages [14.5 kB]
Get:24 http://in.archive.ubuntu.com precise-backports/multiverse amd64 Packages [2,489 B]
Get:25 http://in.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]
Get:26 http://in.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:27 http://in.archive.ubuntu.com precise-backports/universe i386 Packages [14.5 kB]
Get:28 http://in.archive.ubuntu.com precise-backports/multiverse i386 Packages [2,504 B]
Hit http://in.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://in.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://in.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://in.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://in.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://in.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 1,553 kB in 16s (91.7 kB/s)                                            
Reading package lists... Done
gaurav@gaurav-gamma:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.15-0ubuntu10.2)
 libc6:i386 : Depends: libc-bin:i386 (= 2.15-0ubuntu10.2)
 libc6-dev : Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.2 is installed
 libc6-i386 : Depends: libc6 (= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.2 is installed
E: Unmet dependencies. Try using -f.
gaurav@gaurav-gamma:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
3 not fully installed or removed.
Need to get 8,593 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 i386 2.15-0ubuntu10.3 [3,940 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.3 [4,653 kB]
Fetched 8,593 kB in 1min 7s (127 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What would be the reason behind 

> 
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
 

I get the same error for all of my broken packages. If I try to re-install `man-db`, I get the same error. What can be causing this? Even if I run `dpkg --configure -a --debug 777` I get no further detail why the pre-installation script is failing for them. 

More information: 

```

gaurav@gaurav-gamma:~$ sudo dpkg --configure -a 
dpkg: dependency problems prevent configuration of libc6-dev:
 libc6-dev depends on libc6 (= 2.15-0ubuntu10.3); however:
  Version of libc6 on system is 2.15-0ubuntu10.2.
dpkg: error processing libc6-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libc-dev-bin (2.15-0ubuntu10.3) ...
dpkg: dependency problems prevent configuration of libc6-i386:
 libc6-i386 depends on libc6 (= 2.15-0ubuntu10.3); however:
  Version of libc6 on system is 2.15-0ubuntu10.2.
dpkg: error processing libc6-i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev
 libc6-i386

```

Should I re-install the libc package?

---

### Post by AlexDudko on 2012-10-20
You've got libc6 version 2.15-0ubuntu10.2 installed, but it should be 2.15-0ubuntu10.3. Try to download and force upgrade them first (mind that you've got both i386 and amd64 architectures). After that repeat the update normally.
It would be better to disable all additional repositories (ppa's, backports and the rest) so that it was easier to trace the problem.

---

### Post by GVRV on 2012-10-20
> **AlexDudko said:**
> You've got libc6 version 2.15-0ubuntu10.2 installed, but it should be 2.15-0ubuntu10.3. Try to download and force upgrade them first (mind that you've got both i386 and amd64 architectures). After that repeat the update normally.
It would be better to disable all additional repositories (ppa's, backports and the rest) so that it was easier to trace the problem.
Can you please tell me how I should go about it? I cannot apt-get remove libc6, and install -f gives me the errors I posted above. How can I correct them? Thanks.

---

### Post by raja.genupula on 2012-10-20
do the same > dpkg -r for the above two packages and follow the remaining instructions .

---

### Post by GVRV on 2012-10-21
> **raja.genupula said:**
> do the same  for the above two packages and follow the remaining instructions .
I cannot dpkg -r libc6 because heaps of packages depend upon it. I cannot -r  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb and sudo rm -rf  /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb because then if I do apt-get install -f, I get the same error again. 

How do I get rid of this web of unmet dependencies? 

```

gaurav@gaurav-gamma:~$ sudo apt-get install libc6 --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Breaks: libc6:i386 (!= 2.15-0ubuntu10.3) but 2.15-0ubuntu10.2 is to be installed
 libc6:i386 : Depends: libc-bin:i386 (= 2.15-0ubuntu10.2)
              Breaks: libc6 (!= 2.15-0ubuntu10.2) but 2.15-0ubuntu10.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So 2.15-0ubuntu10.2 is needed to satisfy libc6-bin's dependency, but then the broken packages need 2.15-0ubuntu10.3

How do I go about this? Thanks.

---

### Post by AlexDudko on 2012-10-21
> **GVRV said:**
> Can you please tell me how I should go about it? I cannot apt-get remove libc6, and install -f gives me the errors I posted above. How can I correct them? Thanks.

Download packages with proper versions from [here]("http://packages.ubuntu.com/").
And use **dpkg** command to remove conflicting packages and installing the downloaded ones. You may need --force option. So, to remove libc6-i386 package command would be:
> sudo dpkg -r --force-depends libc6-i386
This command will remove the package even though there is a dependency problem.
And use dpkg to install packages:
> sudo dpkg -i --force-depends libc6-i386_2.15-0ubuntu10_amd64.deb


---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> Download packages with proper versions from [here]("http://packages.ubuntu.com/").
And use **dpkg** command to remove conflicting packages and installing the downloaded ones. You may need --force option. So, to remove libc6-i386 package command would be:

This command will remove the package even though there is a dependency problem.
And use dpkg to install packages:
Sorry to sound like a complete noob, but I'm still not quite sure *which* packages do I need to completely remove and then install using the package site? 

Do I install the precise packages from the site, or precise-security packages or precise-updates packages? Should I post the contents of my sources.list so you can have a better idea of how I got into this dependency mess in the first place?

Thanks for your help. Much appreciated. :)

EDIT: Contents of /etc/apt/sources.list in case it helps 

```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise universe
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

---

### Post by AlexDudko on 2012-10-21
See the versions of packages I pointed at above. It should be precise-updates.
I'd remove first libc6-i386 package with all its dependencies to narrow procedures.

---

### Post by AlexDudko on 2012-10-21
> **GVRV said:**
> Sorry to sound like a complete noob, but I'm still not quite sure *which* packages do I need to completely remove and then install using the package site? 

Do I install the precise packages from the site, or precise-security packages or precise-updates packages? Should I post the contents of my sources.list so you can have a better idea of how I got into this dependency mess in the first place?

Thanks for your help. Much appreciated. :)

EDIT: Contents of /etc/apt/sources.list in case it helps 

```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise universe
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://in.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse #Added by software-properties

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

According to your previous posts there are some other repositories enabled, look for them in /etc/apt/sources.list.d directory.

---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> See the versions of packages I pointed at above. It should be precise-updates.
I'd remove first libc6-i386 package with all its dependencies to narrow procedures.
Output of me trying to remove the packages: 

```

gaurav@gaurav-gamma:~$ sudo dpkg -r --force-depends libc6-i386
dpkg: warning: there's no installed package matching libc6-i386
gaurav@gaurav-gamma:~$ sudo dpkg -r --force-depends libc6-amd64
dpkg: warning: there's no installed package matching libc6-amd64
gaurav@gaurav-gamma:~$ sudo dpkg -r --force-depends libc6-dev
dpkg: warning: there's no installed package matching libc6-dev
gaurav@gaurav-gamma:~$ sudo dpkg -r --force-depends libc6-bin
dpkg: warning: there's no installed package matching libc6-bin

```

Output of apt-get install -f 

```

gaurav@gaurav-gamma:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6:i386 libc6-dev libc6-i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6-dev libc6-i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
Need to get 0 B/15.5 MB of archives.
After this operation, 21.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 365163 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I need to find all of these packages on the ubuntu packages site under precise-updates: 

```

The following extra packages will be installed:
  libc6 libc6:i386 libc6-dev libc6-i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6-dev libc6-i386
The following packages will be upgraded:
  libc6 libc6:i386

```

---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> According to your previous posts there are some other repositories enabled, look for them in /etc/apt/sources.list.d directory.
Yup, that's correct, here's the output of `cat *` for /etc/apt/sources.list.d/ directory 

```

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://ppa.launchpad.net/juju/pkgs/ubuntu precise main
deb-src http://ppa.launchpad.net/juju/pkgs/ubuntu precise main
deb http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
deb-src http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
deb http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main
deb-src http://ppa.launchpad.net/pitti/postgresql/ubuntu precise main

```

---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> See the versions of packages I pointed at above. It should be precise-updates.
I'd remove first libc6-i386 package with all its dependencies to narrow procedures.
When I am trying to install the packages from the website, I still get an error. Here's what happens: 

```

gaurav@gaurav-gamma:~/tmp$ sudo dpkg -i --force-depends /home/gaurav/Downloads/libc6_2.15-0ubuntu10.3_i386.deb 
(Reading database ... 365163 files and directories currently installed.)
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /home/gaurav/Downloads/libc6_2.15-0ubuntu10.3_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /home/gaurav/Downloads/libc6_2.15-0ubuntu10.3_i386.deb

```

I could successfully install libc6-bin using the package on the website, I was then planning on installing libc6, then libc6-amd64 and libc6-i386 and finally libc6-dev. But I'm stuck on this error. 

I still have no idea how my packages ended up in this inconsistent situation. Is it a configuration issue?

---

### Post by AlexDudko on 2012-10-21
Please, comment all your ppa's first. There are also some duplicate repositories (Google, for example), it shouldn't be so.
Comment them all and do:
> sudo apt-get clean
sudo apt-get install -f

Do you have Synaptic Package manager installed? Can you install it? If yes, it could help you as well.

---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> Please, comment all your ppa's first. There are also some duplicate repositories (Google, for example), it shouldn't be so.
Comment them all and do:


Do you have Synaptic Package manager installed? Can you install it? If yes, it could help you as well.
I disabled all PPAs (From software center -> Edit -> Software sources) and then I tried to do apt-get clean, apt-get update, apt-get install -f, still no luck. We end up with the same error. 

```

gaurav@gaurav-gamma:~$ sudo apt-get clean
[sudo] password for gaurav: 
gaurav@gaurav-gamma:~$ sudo apt-get update
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://archive.ubuntu.com precise InRelease                                
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://archive.ubuntu.com precise Release.gpg                              
Ign http://in.archive.ubuntu.com precise InRelease
Ign http://in.archive.ubuntu.com precise-updates InRelease
Hit http://security.ubuntu.com precise-security Release
Hit http://security.ubuntu.com precise-security/restricted Sources    
Hit http://archive.ubuntu.com precise Release  
Hit http://in.archive.ubuntu.com precise Release.gpg                  
Hit http://security.ubuntu.com precise-security/main Sources          
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/main amd64 Packages
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Get:1 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://in.archive.ubuntu.com precise Release                     
Hit http://archive.ubuntu.com precise/restricted Sources              
Hit http://security.ubuntu.com precise-security/main Translation-en   
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:2 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://in.archive.ubuntu.com precise/restricted Sources
Hit http://in.archive.ubuntu.com precise/main Sources
Hit http://in.archive.ubuntu.com precise/multiverse Sources
Hit http://in.archive.ubuntu.com precise/universe Sources
Hit http://in.archive.ubuntu.com precise/main amd64 Packages
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://in.archive.ubuntu.com precise/main i386 Packages
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages
Hit http://in.archive.ubuntu.com precise/universe i386 Packages                
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://in.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex             
Get:3 http://in.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]
Get:4 http://in.archive.ubuntu.com precise-updates/main Sources [178 kB]       
Get:5 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]
Get:6 http://in.archive.ubuntu.com precise-updates/universe Sources [60.2 kB]  
Get:7 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [405 kB]
Get:8 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]
Get:9 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [149 kB]
Get:10 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]
Get:11 http://in.archive.ubuntu.com precise-updates/main i386 Packages [410 kB]
Get:12 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:13 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [149 kB]
Get:14 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://in.archive.ubuntu.com precise/main Translation-en                   
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://in.archive.ubuntu.com precise/restricted Translation-en             
Hit http://in.archive.ubuntu.com precise/universe Translation-en               
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en       
Fetched 1,445 kB in 18s (78.1 kB/s)                                            
Reading package lists... Done
gaurav@gaurav-gamma:~$ 
gaurav@gaurav-gamma:~$ git status
fatal: Not a git repository (or any of the parent directories): .git
gaurav@gaurav-gamma:~$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6:i386 libc6-dev libc6-i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6-dev libc6-i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 2 newly installed, 0 to remove and 25 not upgraded.
Need to get 15.5 MB of archives.
After this operation, 21.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 i386 2.15-0ubuntu10.3 [3,940 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6 amd64 2.15-0ubuntu10.3 [4,653 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-dev amd64 2.15-0ubuntu10.3 [2,945 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.3 [3,993 kB]
Fetched 15.5 MB in 1min 28s (175 kB/s)                                         
Preconfiguring packages ...
(Reading database ... 365163 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no clue what is happening :/

Debug statements from trying to install libc6 

```

gaurav@gaurav-gamma:~/www/PHP/v2.atuninow$ sudo dpkg -i --force-depends --debug 777 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
(Reading database ... 365163 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
D000200: process_archive conffile `/etc/ld.so.conf.d/x86_64-linux-gnu.conf' in package libc6 - conff ?
D000020: process_archive conffile `/etc/ld.so.conf.d/x86_64-linux-gnu.conf' package=libc6 same hash=593ad12389ab2b6f952e7ede67b8fbbf
D000200: oldconffsetflags `/etc/ld.so.conf.d/x86_64-linux-gnu.conf' namenode 0x628e090 flags 5
D000001: process_archive oldversionstatus=installed
D000002: fork/exec /var/lib/dpkg/info/libc6:amd64.prerm ( upgrade 2.15-0ubuntu10.3 )
De-configuring libc6:i386 ...
D000002: fork/exec /var/lib/dpkg/info/libc6:i386.prerm ( deconfigure in-favour libc6 2.15-0ubuntu10.3 )
D000002: fork/exec /var/lib/dpkg/tmp.ci/preinst ( upgrade 2.15-0ubuntu10.2 )
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
D000002: fork/exec /var/lib/dpkg/tmp.ci/postrm ( abort-upgrade 2.15-0ubuntu10.2 )
D000002: fork/exec /var/lib/dpkg/info/libc6:i386.postinst ( abort-deconfigure in-favour libc6 2.15-0ubuntu10.3 )
D000002: fork/exec /var/lib/dpkg/info/libc6:amd64.postinst ( abort-upgrade 2.15-0ubuntu10.3 )
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/tmp.ci'
D000010: ensure_pathname_nonexisting running rm -rf
D000010: ensure_pathname_nonexisting `/var/lib/dpkg/reassemble.deb'
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb

```

---

### Post by AlexDudko on 2012-10-21
Do you have Synaptic Package Manager? Can you install and launch it? It could give you some clues.

---

### Post by GVRV on 2012-10-21
> **AlexDudko said:**
> Do you have Synaptic Package Manager? Can you install and launch it? It could give you some clues.
I don't have it and I cannot install anything from my Software Center anymore as well. It thinks the catalog is broken, if I try to 'repair', I get the same error as I've pasted. 

Any ideas?

---

### Post by funicorn on 2012-10-21
What's going above is textbook on how to destroy an operation system by hand. Please stop any operation on libc6, it's the most lethal package of your system.

Have you ever tried 'apt-get -f install' ?

---

### Post by GVRV on 2012-10-21
> **funicorn said:**
> What's going above is textbook on how to destroy an operation system by hand. Please stop any operation on libc6, it's the most lethal package of your system.

Have you ever tried 'apt-get -f install' ?
Which I now regretfully realize. Though, I did say I didn't have any clue on what I was doing, I was pretty much just following instructions. 

`apt-get install -f` does not fix this mess, it just leads to more errors as can be seen here: [http://paste.ubuntu.com/1294497/](http://paste.ubuntu.com/1294497/)

I spent some time in #ubuntu on Freenode, and the general consensus seemed to be the installation is royally screwed, and a re-install is in order, unless you have a solution?

---

### Post by flipperwald on 2012-10-23
I had more or less the same challenge. This worked for me:

root@twosheds:/home/staalej# ls *deb
libc6_2.15-0ubuntu10.2_i386.deb  libc6-dev_2.15-0ubuntu10.2_i386.deb  libc-bin_2.15-0ubuntu10.2_i386.deb  libc-dev-bin_2.15-0ubuntu10.2_i386.deb
root@twosheds:/home/staalej# dpkg -i  *deb
(Reading database ... 334533 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using libc6_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6 ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: warning: downgrading libc-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using libc-bin_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: warning: downgrading libc-dev-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-dev-bin 2.15-0ubuntu10.3 (using libc-dev-bin_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
Processing triggers for man-db ...
Setting up libc6 (2.15-0ubuntu10.2) ...
Setting up libc-dev-bin (2.15-0ubuntu10.2) ...
Setting up libc6-dev (2.15-0ubuntu10.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@twosheds:/home/staalej# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up build-essential (11.5ubuntu2.1) ...
root@twosheds:/home/staalej# dpkg --configure -a
root@twosheds:/home/staalej# apt-get clean
root@twosheds:/home/staalej# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@twosheds:/home/staalej#

I downloaded the old versions of the libraries and installed
them at the same time. This seems to have done the trick. I'm on a i386 system. The server just booted successfully, at least :o

Best of luck,

--
Ståle

---

### Post by GVRV on 2012-10-23
> **flipperwald said:**
> I had more or less the same challenge. This worked for me:

root@twosheds:/home/staalej# ls *deb
libc6_2.15-0ubuntu10.2_i386.deb  libc6-dev_2.15-0ubuntu10.2_i386.deb  libc-bin_2.15-0ubuntu10.2_i386.deb  libc-dev-bin_2.15-0ubuntu10.2_i386.deb
root@twosheds:/home/staalej# dpkg -i  *deb
(Reading database ... 334533 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using libc6_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6 ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using libc6-dev_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg: warning: downgrading libc-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using libc-bin_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg: warning: downgrading libc-dev-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-dev-bin 2.15-0ubuntu10.3 (using libc-dev-bin_2.15-0ubuntu10.2_i386.deb) ...
Unpacking replacement libc-dev-bin ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
Processing triggers for man-db ...
Setting up libc6 (2.15-0ubuntu10.2) ...
Setting up libc-dev-bin (2.15-0ubuntu10.2) ...
Setting up libc6-dev (2.15-0ubuntu10.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
root@twosheds:/home/staalej# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up build-essential (11.5ubuntu2.1) ...
root@twosheds:/home/staalej# dpkg --configure -a
root@twosheds:/home/staalej# apt-get clean
root@twosheds:/home/staalej# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@twosheds:/home/staalej#

I downloaded the old versions of the libraries and installed
them at the same time. This seems to have done the trick. I'm on a i386 system. The server just booted successfully, at least :o

Best of luck,

--
Ståle
Thanks your input. So I should just grab the .deb files for all my packages that are broken? My apt-get install -f shows: 

```

The following extra packages will be installed:
  libc6 libc6:i386 libc6-dev libc6-i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6-dev libc6-i386
The following packages will be upgraded:
  libc6 libc6:i386

```

What is the 'libc6:i386' package? I'm on a amd64 system, I'll try your approach and update. Thanks! :)

---

### Post by flipperwald on 2012-10-24
> **GVRV said:**
> Thanks your input. So I should just grab the .deb files for all my packages that are broken? My apt-get install -f shows: 

```

The following extra packages will be installed:
  libc6 libc6:i386 libc6-dev libc6-i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following NEW packages will be installed:
  libc6-dev libc6-i386
The following packages will be upgraded:
  libc6 libc6:i386

```

What is the 'libc6:i386' package? I'm on a amd64 system, I'll try your approach and update. Thanks! :)

I'm not sure what that package is. Basically, I have the impression that dpkg will sort out the dependencies between all the packages on the command line. I suggest something like

dpkg -i libc6 libc6-dev libc6-i386

for the same generation of these packages. If dpkg is happy, they will install, otherwise it may tell you it wants another package also.

-- 
Ståle

---

### Post by GVRV on 2012-10-25
> **flipperwald said:**
> I'm not sure what that package is. Basically, I have the impression that dpkg will sort out the dependencies between all the packages on the command line. I suggest something like

dpkg -i libc6 libc6-dev libc6-i386

for the same generation of these packages. If dpkg is happy, they will install, otherwise it may tell you it wants another package also.

-- 
Ståle
Okay, that *seems* to have worked even though there were errors in there. I'll try updating and upgrading and installing a new package now to see if APT is really back to normal

```

(k3)gaurav@gaurav-gamma:~/Downloads$ ls libc*
libc6_2.15-0ubuntu10.2_amd64.deb  libc6-dev_2.15-0ubuntu10.2_amd64.deb   libc-bin_2.15-0ubuntu10.2_amd64.deb
libc6_2.15-0ubuntu10.2_i386.deb   libc6-i386_2.15-0ubuntu10.2_amd64.deb  libc-dev-bin_2.15-0ubuntu10.2_amd64.deb
(k3)gaurav@gaurav-gamma:~/Downloads$ sudo dpkg -i libc*
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using libc6_2.15-0ubuntu10.2_amd64.deb) ...
dpkg: error processing libc6_2.15-0ubuntu10.2_amd64.deb (--install):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using libc6_2.15-0ubuntu10.2_i386.deb) ...
dpkg: error processing libc6_2.15-0ubuntu10.2_i386.deb (--install):
 subprocess new pre-installation script returned error exit status 1
dpkg: warning: downgrading libc6-dev from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc6-dev 2.15-0ubuntu10.3 (using libc6-dev_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6-dev ...
dpkg: warning: downgrading libc6-i386 from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc6-i386 2.15-0ubuntu10.3 (using libc6-i386_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Replaced by files in installed package libc6:i386 ...
dpkg: warning: downgrading libc-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-bin 2.15-0ubuntu10.3 (using libc-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-bin ...
dpkg: warning: downgrading libc-dev-bin from 2.15-0ubuntu10.3 to 2.15-0ubuntu10.2.
Preparing to replace libc-dev-bin 2.15-0ubuntu10.3 (using libc-dev-bin_2.15-0ubuntu10.2_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Setting up libc6-i386 (2.15-0ubuntu10.2) ...
Setting up libc-bin (2.15-0ubuntu10.2) ...
Setting up libc-dev-bin (2.15-0ubuntu10.2) ...
Setting up libc6-dev (2.15-0ubuntu10.2) ...
Errors were encountered while processing:
 libc6_2.15-0ubuntu10.2_amd64.deb
 libc6_2.15-0ubuntu10.2_i386.deb
(k3)gaurav@gaurav-gamma:~/Downloads$ sudo apt-get install -f 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 47 not upgraded.
(k3)gaurav@gaurav-gamma:~/Downloads$ sudo dpkg --configure -a

```

---

### Post by GVRV on 2012-10-25
Nope, upgrading fails and gives us the same error. Why is the 'libc6:i386' package update screwing up all the damn time? 

```

(k3)gaurav@gaurav-gamma:~/Downloads$ sudo apt-get update
Ign http://archive.ubuntu.com precise InRelease                                            
Ign http://in.archive.ubuntu.com precise InRelease
Ign http://in.archive.ubuntu.com precise-updates InRelease
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://in.archive.ubuntu.com precise Release.gpg
Hit http://archive.ubuntu.com precise Release
Get:1 http://in.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise/main Sources        
Hit http://in.archive.ubuntu.com precise Release
Hit http://archive.ubuntu.com precise/restricted Sources
Get:2 http://in.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://in.archive.ubuntu.com precise/restricted Sources
Hit http://in.archive.ubuntu.com precise/main Sources
Hit http://in.archive.ubuntu.com precise/multiverse Sources
Hit http://in.archive.ubuntu.com precise/universe Sources
Hit http://in.archive.ubuntu.com precise/main amd64 Packages
Hit http://in.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://in.archive.ubuntu.com precise/universe amd64 Packages
Hit http://in.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://in.archive.ubuntu.com precise/main i386 Packages
Hit http://in.archive.ubuntu.com precise/restricted i386 Packages
Hit http://in.archive.ubuntu.com precise/universe i386 Packages
Hit http://in.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://in.archive.ubuntu.com precise/main TranslationIndex
Hit http://in.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://in.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://in.archive.ubuntu.com precise/universe TranslationIndex
Get:3 http://in.archive.ubuntu.com precise-updates/restricted Sources [4,395 B]                                                                    
Get:4 http://in.archive.ubuntu.com precise-updates/main Sources [179 kB]                                                                           
Get:5 http://in.archive.ubuntu.com precise-updates/multiverse Sources [4,745 B]                                                                    
Get:6 http://in.archive.ubuntu.com precise-updates/universe Sources [60.2 kB]                                                                      
Get:7 http://in.archive.ubuntu.com precise-updates/main amd64 Packages [406 kB]                                                                    
Get:8 http://in.archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]                                                             
Get:9 http://in.archive.ubuntu.com precise-updates/universe amd64 Packages [149 kB]                                                                
Get:10 http://in.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]                                                            
Get:11 http://in.archive.ubuntu.com precise-updates/main i386 Packages [412 kB]                                                                    
Get:12 http://in.archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]                                                             
Get:13 http://in.archive.ubuntu.com precise-updates/universe i386 Packages [150 kB]                                                                
Get:14 http://in.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]                                                             
Hit http://in.archive.ubuntu.com precise-updates/main TranslationIndex                                                                             
Hit http://in.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                       
Hit http://in.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                       
Hit http://in.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                         
Hit http://in.archive.ubuntu.com precise/main Translation-en                                                                                       
Hit http://in.archive.ubuntu.com precise/multiverse Translation-en                                                                                 
Hit http://in.archive.ubuntu.com precise/restricted Translation-en                                                                                 
Hit http://in.archive.ubuntu.com precise/universe Translation-en                                                                                   
Hit http://in.archive.ubuntu.com precise-updates/main Translation-en                                                                               
Hit http://in.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                         
Hit http://in.archive.ubuntu.com precise-updates/restricted Translation-en                                                                         
Hit http://in.archive.ubuntu.com precise-updates/universe Translation-en                                                                           
Fetched 1,451 kB in 18s (76.9 kB/s)                                                                                                                
Reading package lists... Done
(k3)gaurav@gaurav-gamma:~/Downloads$ 
(k3)gaurav@gaurav-gamma:~/Downloads$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor apport apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon aptdaemon-data libapt-inst1.4 libapt-pkg4.12 libc-bin
  libc-dev-bin libc6 libc6:i386 libc6-dev libc6-i386 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-glx:i386 libglapi-mesa
  libglapi-mesa:i386 libglu1-mesa libglu1-mesa:i386 libldap-2.4-2 libldap-2.4-2:i386 libparted0debian1 libxatracker1 lsb-base lsb-release
  multiarch-support onboard parted passwd python-apport python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-problem-report sessioninstaller update-notifier update-notifier-common wpasupplicant x11-utils xserver-xorg-input-wacom
  xserver-xorg-video-intel
47 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 22.0 MB/30.6 MB of archives.
After this operation, 37.9 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc-bin amd64 2.15-0ubuntu10.3 [1,181 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.3 [3,993 kB]                                       
Get:3 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc-dev-bin amd64 2.15-0ubuntu10.3 [84.5 kB]                                      
Get:4 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libc6-dev amd64 2.15-0ubuntu10.3 [2,945 kB]                                        
Get:5 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.5 [939 kB]                               
Get:6 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apt amd64 0.8.16~exp12ubuntu10.5 [1,100 kB]                                        
Get:7 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.5 [99.8 kB]                              
Get:8 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-base all 4.0-0ubuntu20.2 [10.4 kB]                                             
Get:9 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apparmor amd64 2.7.102-0ubuntu3.2 [357 kB]                                         
Get:10 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libldap-2.4-2 i386 2.4.28-1.1ubuntu4.2 [186 kB]                                   
Get:11 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libldap-2.4-2 amd64 2.4.28-1.1ubuntu4.2 [186 kB]                                  
Get:12 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libparted0debian1 amd64 2.3-8ubuntu5.1 [240 kB]                                   
Get:13 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dri amd64 8.0.4-0ubuntu0.1 [3,056 kB]                                 
Get:14 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-dri i386 8.0.4-0ubuntu0.1 [3,098 kB]                                  
Get:15 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-glx i386 8.0.4-0ubuntu0.1 [103 kB]                                    
Get:16 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libgl1-mesa-glx amd64 8.0.4-0ubuntu0.1 [104 kB]                                   
Get:17 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglapi-mesa amd64 8.0.4-0ubuntu0.1 [21.1 kB]                                    
Get:18 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglapi-mesa i386 8.0.4-0ubuntu0.1 [21.1 kB]                                     
Get:19 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libxatracker1 amd64 8.0.4-0ubuntu0.1 [351 kB]                                     
Get:20 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier amd64 0.119ubuntu8.6 [57.3 kB]                                    
Get:21 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main update-notifier-common all 0.119ubuntu8.6 [222 kB]                                
Get:22 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglu1-mesa i386 8.0.4-0ubuntu0.1 [165 kB]                                       
Get:23 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main libglu1-mesa amd64 8.0.4-0ubuntu0.1 [161 kB]                                      
Get:24 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main multiarch-support amd64 2.15-0ubuntu10.3 [4,480 B]                                
Get:25 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main passwd amd64 1:4.1.4.2+svn3283-3ubuntu5.1 [959 kB]                                
Get:26 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apt-utils amd64 0.8.16~exp12ubuntu10.5 [190 kB]                                   
Get:27 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-release all 4.0-0ubuntu20.2 [10.8 kB]                                         
Get:28 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apt-transport-https amd64 0.8.16~exp12ubuntu10.5 [16.3 kB]                        
Get:29 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main parted amd64 2.3-8ubuntu5.1 [52.4 kB]                                             
Get:30 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu14 [9,882 B]                               
Get:31 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu14 [79.6 kB]                                       
Get:32 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu14 [145 kB]                                               
Get:33 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu14 [9,224 B]                                          
Get:34 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main apport-symptoms all 0.16.1 [14.2 kB]                                              
Get:35 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main onboard amd64 0.97.0-0ubuntu4 [406 kB]                                            
Get:36 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main wpasupplicant amd64 0.7.3-6ubuntu2.1 [490 kB]                                     
Get:37 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main x11-utils amd64 7.6+4ubuntu0.1 [230 kB]                                           
Get:38 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-input-wacom amd64 1:0.14.0-0ubuntu2.1 [88.0 kB]                      
Get:39 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main xserver-xorg-video-intel amd64 2:2.17.0-1ubuntu4.2 [238 kB]                       
Get:40 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main aptdaemon-data all 0.43+bzr805-0ubuntu5 [164 kB]                                  
Get:41 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon.gtk3widgets all 0.43+bzr805-0ubuntu5 [14.9 kB]                   
Get:42 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon.pkcompat all 0.43+bzr805-0ubuntu5 [29.1 kB]                      
Get:43 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main aptdaemon all 0.43+bzr805-0ubuntu5 [14.7 kB]                                      
Get:44 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main python-aptdaemon all 0.43+bzr805-0ubuntu5 [82.5 kB]                               
Get:45 http://in.archive.ubuntu.com/ubuntu/ precise-updates/main sessioninstaller all 0.20+bzr128-0ubuntu1.2 [29.7 kB]                             
Fetched 22.0 MB in 3min 10s (115 kB/s)                                                                                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
apparmor failed to preconfigure, with exit status 1
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc-bin 2.15-0ubuntu10.2 (using .../libc-bin_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc-bin ...
Setting up libc-bin (2.15-0ubuntu10.3) ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6-i386 2.15-0ubuntu10.2 (using .../libc6-i386_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6-i386 ...
Replaced by files in installed package libc6:i386 ...
Preparing to replace libc-dev-bin 2.15-0ubuntu10.2 (using .../libc-dev-bin_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc-dev-bin ...
Preparing to replace libc6-dev 2.15-0ubuntu10.2 (using .../libc6-dev_2.15-0ubuntu10.3_amd64.deb) ...
Unpacking replacement libc6-dev ...
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
(k3)gaurav@gaurav-gamma:~/Downloads$ 
(k3)gaurav@gaurav-gamma:~/Downloads$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 libc6:i386
Suggested packages:
  glibc-doc glibc-doc:i386 locales:i386
The following packages will be upgraded:
  libc6 libc6:i386
2 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
3 not fully installed or removed.
Need to get 0 B/8,593 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
(Reading database ... 365946 files and directories currently installed.)
Preparing to replace libc6 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_amd64.deb) ...
De-configuring libc6:i386 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Preparing to replace libc6:i386 2.15-0ubuntu10.2 (using .../libc6_2.15-0ubuntu10.3_i386.deb) ...
De-configuring libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_amd64.deb
 /var/cache/apt/archives/libc6_2.15-0ubuntu10.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dino99 on 2012-10-25
its due to multiarch actual config, dont worry. But i feel like you have pushed the bigest mess there, and i doubt you will get it working back smootly now :(:(

if you still want to try fixing it before doing a fresh clean reinstall, then try:

sudo apt-get install --reinstall dpkg gcc cpp udev ubuntu-desktop

---

### Post by GVRV on 2012-10-25
> **dino99 said:**
> its due to multiarch actual config, dont worry. But i feel like you have pushed the bigest mess there, and i doubt you will get it working back smootly now :(:(

if you still want to try fixing it before doing a fresh clean reinstall, then try:

sudo apt-get install --reinstall dpkg gcc cpp udev ubuntu-desktop
Didn't really do anything. 

```

(k3)gaurav@gaurav-gamma:~/Downloads$ sudo apt-get install --reinstall dpkg gcc cpp udev ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-user-guide man-db ubuntu-docs yelp
Suggested packages:
  groff ttf-dejavu
The following NEW packages will be installed:
  gnome-user-guide man-db ubuntu-desktop ubuntu-docs yelp
0 upgraded, 5 newly installed, 4 reinstalled, 0 to remove and 47 not upgraded.
Need to get 0 B/6,206 kB of archives.
After this operation, 65.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(k3)gaurav@gaurav-gamma:~/Downloads$ 

```

Yeah, I'm just gonna suck it up and try upgrading to 12.10 over the weekend, if even the dist-upgrade fails, I'm bracing for a clean re-install :(

---

### Post by AlexDudko on 2012-10-25
It could be caused by some package, installed manually or from some ppa repository which conflicts with other base system packages from official repositories. Everything cold be OK while installing it, but now it still depends on some older versions of packages and prevents system upgrades, causing this failure.
Try to remember which packages you have installed not from the official repositories and remove them.

---

### Post by Damascushead on 2012-10-25
Just read through this thread and am having the same problem. It occurs when I try to upgrade and when I try to get pretty much anything from any repository, but specifically with java and OpenMPI. It is driving me nuts!!

[http://ubuntuforums.org/showthread.php?t=2076329](http://ubuntuforums.org/showthread.php?t=2076329)

Good luck with the upgrade/clean install. It will be interesting to see if that fixes the error.

---

### Post by GVRV on 2012-10-28
Like mentioned before, I updated my system to 12.10 today and it seems to have fixed the APT dependency hell. Being careful not adding new PPAs now. Thanks for the help everyone! :)

---

### Post by anshuhim20 on 2012-10-29
I have been trying to install fslview with the command the error msg comes "Unable to correct problems, you have held broken packages" 
I am sending the details also


sudo apt-get install fslview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 fslview : Depends: libvtk5.4 but it is not installable
           Depends: libvtk5.4-qt4 but it is not installable
           Recommends: fslview-doc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


please suggest appropriate ely

---

### Post by Mobidoy on 2012-10-29
I had a similar issue with nvidia-current see [This thread]("http://ubuntuforums.org/showthread.php?t=2077451"). What I did to solve it was to download the package manualy and install it with dpkg -i.

---

