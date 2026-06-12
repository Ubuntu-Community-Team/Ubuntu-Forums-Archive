---
title: "libgbm1 kept back during upgrade"
date: 2016-02-21
forum: Installation &amp; Upgrades
---

### Post by Spencer_Thompson on 2016-02-21
Hello! When I upgrade my packages in the terminal, it tells me I have one package kept back - libgbm1. Is there a reason why this package has been kept back and a way to fix this? I am running Ubuntu 14.04.4. If you ask me to do something, please give some instructions as I don't know much about Ubuntu.

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgbm1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by ian-weisser on 2016-02-21
Try the following. If it fails, please show us the complete output
```
sudo apt full-upgrade
```
This is equivalent to the older 'apt-get dist-upgrade' command.

---

### Post by Bucky Ball on 2016-02-21
Did you:

> sudo apt-get update

... first? You should always run that before any upgrade command. 

PS: I have taken the liberty of changing your thread title to increase the likelihood of you getting support. Generic thread titles like 'libgbm1' tell potential helpers nothing about your actual issue. ;)

Good luck. :)

---

### Post by Spencer_Thompson on 2016-02-22
I always update my packages before upgrading them. I have run the command and got the following result. @ian-weisser
```
$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgbm1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

Also, thanks for changing my title. I'll be sure to have more details in future threads.

---

### Post by Spencer_Thompson on 2016-02-23
Bump.

---

### Post by ian-weisser on 2016-02-23
Did you try Post #2?

---

### Post by Spencer_Thompson on 2016-02-23
Yes, I updated then tried upgrading and got the same result.

---

### Post by QLee on 2016-02-23
Maybe this is a good time to see what the system thinks about libgbm1.  
Post the results of this code run in a terminal ```
apt-cache policy libgbm1 
```

---

### Post by Spencer_Thompson on 2016-02-23
```
$ apt-cache policy libgbm1
libgbm1:
  Installed: 10.1.3-0ubuntu0.5
  Candidate: 11.2+gallium-nine~git1602220800.9e204a~gd~t
  Version table:
     11.2+gallium-nine~git1602220800.9e204a~gd~t 0
        500 http://ppa.launchpad.net/oibaf/gallium-nine/ubuntu/ trusty/main amd64 Packages
     11.0.4~git20151026+11.0.ec14e6f8-0ubuntu0ricotz~trusty 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ trusty/main amd64 Packages
     10.1.3-0ubuntu0.6 0
        500 http://mirror.symnds.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 10.1.3-0ubuntu0.5 0
        100 /var/lib/dpkg/status
     10.1.0-4ubuntu5 0
        500 http://mirror.symnds.com/ubuntu/ trusty/main amd64 Packages
```

---

### Post by Bucky Ball on 2016-02-23
Well, you have the version from the Xorg.edgers PPA installed by the looks of it, and you have another PPA that's either installed a version or is trying to, and you have the version in the official repos. All of this is probably somehow preventing the one from the repos installing I'd say. Probably a newer version and incompatible with what you're trying to do (install an older version, perhaps?).

Thus the pitfalls of PPAs, at least sometimes, if that is the issue. I suggest you get rid of the two manually added PPAs, probably a result of trying to force lib1 in there, and try a regular update, upgrade, dist-upgrade again.

---

### Post by Spencer_Thompson on 2016-02-23
I deleted the Xorg.edgers PPAs and ran the commands. Here is the result.
```
$ sudo apt-get update
Ign http://mirror.symnds.com trusty InRelease
Ign http://dl.google.com stable InRelease                                      
Hit http://mirror.symnds.com trusty-updates InRelease                          
Hit http://repo.steampowered.com precise InRelease                             
Hit http://dl.google.com stable Release.gpg                                    
Hit http://mirror.symnds.com trusty-backports InRelease                        
Ign http://linux.dropbox.com trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://mirror.symnds.com trusty-security InRelease                         
Hit http://repository.spotify.com stable InRelease                             
Hit http://mirror.symnds.com trusty Release.gpg                                
Hit http://deb.playonlinux.com saucy InRelease                                 
Hit http://dl.google.com stable Release                                        
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://linux.dropbox.com trusty Release.gpg                                
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://mirror.symnds.com trusty-updates/main Sources                       
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://mirror.symnds.com trusty-updates/restricted Sources                 
Hit http://deb.playonlinux.com saucy/main amd64 Packages                       
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://mirror.symnds.com trusty-updates/universe Sources                   
Hit http://mirror.symnds.com trusty-updates/multiverse Sources                 
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://linux.dropbox.com trusty Release                                    
Hit http://mirror.symnds.com trusty-updates/main amd64 Packages                
Hit http://deb.playonlinux.com saucy/main i386 Packages                        
Hit http://archive.canonical.com trusty Release                                
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://mirror.symnds.com trusty-updates/restricted amd64 Packages          
Hit http://mirror.symnds.com trusty-updates/universe amd64 Packages            
Hit http://mirror.symnds.com trusty-updates/multiverse amd64 Packages          
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://linux.dropbox.com trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty-updates/main i386 Packages                 
Hit http://mirror.symnds.com trusty-updates/restricted i386 Packages           
Hit http://mirror.symnds.com trusty-updates/universe i386 Packages             
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty-updates/multiverse i386 Packages           
Hit http://mirror.symnds.com trusty-updates/main Translation-en                
Hit http://linux.dropbox.com trusty/main i386 Packages                         
Hit http://deb.opera.com stable InRelease                                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit https://deb.opera.com stable InRelease                                     
Hit http://mirror.symnds.com trusty-updates/multiverse Translation-en          
Hit http://deb.opera.com stable InRelease                                      
Hit http://mirror.symnds.com trusty-updates/restricted Translation-en          
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://mirror.symnds.com trusty-updates/universe Translation-en            
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit https://deb.opera.com stable/non-free amd64 Packages                       
Hit http://mirror.symnds.com trusty-backports/main Sources                     
Ign http://dl.google.com stable/main Translation-en                            
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://mirror.symnds.com trusty-backports/restricted Sources               
Hit http://mirror.symnds.com trusty-backports/universe Sources                 
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit https://deb.opera.com stable/non-free i386 Packages                        
Hit http://mirror.symnds.com trusty-backports/multiverse Sources               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://mirror.symnds.com trusty-backports/main amd64 Packages              
Hit http://mirror.symnds.com trusty-backports/restricted amd64 Packages        
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://mirror.symnds.com trusty-backports/universe amd64 Packages          
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://mirror.symnds.com trusty-backports/multiverse amd64 Packages        
Hit http://mirror.symnds.com trusty-backports/main i386 Packages               
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://mirror.symnds.com trusty-backports/restricted i386 Packages         
Hit http://mirror.symnds.com trusty-backports/universe i386 Packages           
Hit http://mirror.symnds.com trusty-backports/multiverse i386 Packages         
Ign http://deb.playonlinux.com saucy/main Translation-en_US                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://mirror.symnds.com trusty-backports/main Translation-en              
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://mirror.symnds.com trusty-backports/multiverse Translation-en        
Hit http://mirror.symnds.com trusty-backports/restricted Translation-en        
Ign http://deb.playonlinux.com saucy/main Translation-en                       
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://linux.dropbox.com trusty/main Translation-en_US                     
Hit http://mirror.symnds.com trusty-backports/universe Translation-en          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty-security/main Sources                      
Ign http://linux.dropbox.com trusty/main Translation-en                        
Hit http://mirror.symnds.com trusty-security/restricted Sources                
Hit http://mirror.symnds.com trusty-security/universe Sources                  
Hit http://mirror.symnds.com trusty-security/multiverse Sources                
Hit http://mirror.symnds.com trusty-security/main amd64 Packages               
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://mirror.symnds.com trusty-security/restricted amd64 Packages         
Hit http://mirror.symnds.com trusty-security/universe amd64 Packages           
Hit http://mirror.symnds.com trusty-security/multiverse amd64 Packages         
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://mirror.symnds.com trusty-security/main i386 Packages                
Hit http://mirror.symnds.com trusty-security/restricted i386 Packages          
Hit http://mirror.symnds.com trusty-security/universe i386 Packages            
Hit http://mirror.symnds.com trusty-security/multiverse i386 Packages          
Ign https://deb.opera.com stable/non-free Translation-en_US                    
Hit http://mirror.symnds.com trusty-security/main Translation-en               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://mirror.symnds.com trusty-security/multiverse Translation-en         
Hit http://mirror.symnds.com trusty-security/restricted Translation-en         
Ign https://deb.opera.com stable/non-free Translation-en                       
Hit http://mirror.symnds.com trusty-security/universe Translation-en           
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://mirror.symnds.com trusty Release                                    
Hit http://ppa.launchpad.net trusty/main Sources                               
Hit http://mirror.symnds.com trusty/main Sources                               
Hit http://mirror.symnds.com trusty/restricted Sources                         
Hit http://mirror.symnds.com trusty/universe Sources                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty/multiverse Sources                         
Hit http://mirror.symnds.com trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty/restricted amd64 Packages                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://mirror.symnds.com trusty/universe amd64 Packages                    
Hit http://mirror.symnds.com trusty/multiverse amd64 Packages                  
Hit http://mirror.symnds.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://mirror.symnds.com trusty/restricted i386 Packages                   
Hit http://mirror.symnds.com trusty/universe i386 Packages                     
Hit http://mirror.symnds.com trusty/multiverse i386 Packages                   
Hit http://ppa.launchpad.net trusty/main Sources                               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://mirror.symnds.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://mirror.symnds.com trusty/multiverse Translation-en                  
Hit http://mirror.symnds.com trusty/restricted Translation-en                  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://mirror.symnds.com trusty/universe Translation-en        
Hit http://ppa.launchpad.net trusty/main Translation-en            
Ign http://deb.opera.com stable/non-free Translation-en_US         
Hit http://ppa.launchpad.net trusty/main Sources                               
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://mirror.symnds.com trusty/main Translation-en_US                     
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Ign http://mirror.symnds.com trusty/multiverse Translation-en_US   
Ign http://mirror.symnds.com trusty/restricted Translation-en_US   
Ign http://deb.opera.com stable/non-free Translation-en            
Hit http://ppa.launchpad.net trusty/main Translation-en            
Ign http://mirror.symnds.com trusty/universe Translation-en_US     
Hit http://ppa.launchpad.net trusty Release                        
Hit http://ppa.launchpad.net trusty/main Sources    
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libgbm1 linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra cpio
  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 libssh-4
  linux-libc-dev opera-stable oxideqt-codecs-extra
11 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 145 MB of archives.
After this operation, 16.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://mirror.symnds.com/ubuntu/ trusty-updates/universe chromium-browser-l10n all 48.0.2564.116-0ubuntu0.14.04.1.1111 [3,290 kB]
Get:2 http://mirror.symnds.com/ubuntu/ trusty-updates/universe chromium-browser amd64 48.0.2564.116-0ubuntu0.14.04.1.1111 [64.2 MB]
Get:3 http://mirror.symnds.com/ubuntu/ trusty-updates/universe chromium-codecs-ffmpeg-extra amd64 48.0.2564.116-0ubuntu0.14.04.1.1111 [881 kB]
Get:4 http://mirror.symnds.com/ubuntu/ trusty-updates/main libssh-4 amd64 0.6.1-0ubuntu3.3 [114 kB]
Get:5 http://mirror.symnds.com/ubuntu/ trusty-updates/main cpio amd64 2.11+dfsg-1ubuntu1.2 [73.8 kB]
Get:6 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-79.123 [776 kB]
Get:7 http://mirror.symnds.com/ubuntu/ trusty-updates/main liboxideqt-qmlplugin amd64 1.12.7-0ubuntu0.14.04.1 [184 kB]
Get:8 http://mirror.symnds.com/ubuntu/ trusty-updates/main liboxideqtquick0 amd64 1.12.7-0ubuntu0.14.04.1 [264 kB]
Get:9 http://mirror.symnds.com/ubuntu/ trusty-updates/main liboxideqtcore0 amd64 1.12.7-0ubuntu0.14.04.1 [29.5 MB]
Get:10 http://mirror.symnds.com/ubuntu/ trusty-updates/main oxideqt-codecs-extra amd64 1.12.7-0ubuntu0.14.04.1 [885 kB]
Fetched 145 MB in 60s (2,407 kB/s)                                             
Preconfiguring packages ...
(Reading database ... 303221 files and directories currently installed.)
Preparing to unpack .../chromium-browser-l10n_48.0.2564.116-0ubuntu0.14.04.1.1111_all.deb ...
Unpacking chromium-browser-l10n (48.0.2564.116-0ubuntu0.14.04.1.1111) over (48.0.2564.82-0ubuntu0.14.04.1.1108) ...
Preparing to unpack .../chromium-browser_48.0.2564.116-0ubuntu0.14.04.1.1111_amd64.deb ...
Unpacking chromium-browser (48.0.2564.116-0ubuntu0.14.04.1.1111) over (48.0.2564.82-0ubuntu0.14.04.1.1108) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_48.0.2564.116-0ubuntu0.14.04.1.1111_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (48.0.2564.116-0ubuntu0.14.04.1.1111) over (48.0.2564.82-0ubuntu0.14.04.1.1108) ...
Preparing to unpack .../libssh-4_0.6.1-0ubuntu3.3_amd64.deb ...
Unpacking libssh-4:amd64 (0.6.1-0ubuntu3.3) over (0.6.1-0ubuntu3.1) ...
Preparing to unpack .../opera-stable_35.0.2066.82_amd64.deb ...
Unpacking opera-stable (35.0.2066.82) over (35.0.2066.68) ...
Preparing to unpack .../cpio_2.11+dfsg-1ubuntu1.2_amd64.deb ...
Unpacking cpio (2.11+dfsg-1ubuntu1.2) over (2.11+dfsg-1ubuntu1.1) ...
Preparing to unpack .../linux-libc-dev_3.13.0-79.123_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-79.123) over (3.13.0-77.121) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqtquick0_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqtcore0_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Preparing to unpack .../oxideqt-codecs-extra_1.12.7-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.12.7-0ubuntu0.14.04.1) over (1.12.6-0ubuntu0.14.04.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Setting up chromium-codecs-ffmpeg-extra (48.0.2564.116-0ubuntu0.14.04.1.1111) ...
Setting up chromium-browser (48.0.2564.116-0ubuntu0.14.04.1.1111) ...
Setting up chromium-browser-l10n (48.0.2564.116-0ubuntu0.14.04.1.1111) ...
Setting up libssh-4:amd64 (0.6.1-0ubuntu3.3) ...
Setting up opera-stable (35.0.2066.82) ...
Setting up cpio (2.11+dfsg-1ubuntu1.2) ...
Setting up linux-libc-dev:amd64 (3.13.0-79.123) ...
Setting up oxideqt-codecs-extra:amd64 (1.12.7-0ubuntu0.14.04.1) ...
Setting up liboxideqtcore0:amd64 (1.12.7-0ubuntu0.14.04.1) ...
Setting up liboxideqtquick0:amd64 (1.12.7-0ubuntu0.14.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.12.7-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.16.0-62 linux-headers-3.16.0-62-generic
  linux-image-3.16.0-62-generic linux-image-extra-3.16.0-62-generic
The following packages have been kept back:
  libgbm1
The following packages will be upgraded:
  linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
3 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 63.6 MB of archives.
After this operation, 280 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-image-3.16.0-62-generic amd64 3.16.0-62.82~14.04.1 [16.2 MB]
Get:2 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-image-extra-3.16.0-62-generic amd64 3.16.0-62.82~14.04.1 [37.6 MB]
Get:3 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-generic-lts-utopic amd64 3.16.0.62.53 [1,804 B]
Get:4 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-image-generic-lts-utopic amd64 3.16.0.62.53 [2,240 B]
Get:5 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-62 all 3.16.0-62.82~14.04.1 [9,059 kB]
Get:6 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-headers-3.16.0-62-generic amd64 3.16.0-62.82~14.04.1 [714 kB]
Get:7 http://mirror.symnds.com/ubuntu/ trusty-updates/main linux-headers-generic-lts-utopic amd64 3.16.0.62.53 [2,224 B]
Fetched 63.6 MB in 27s (2,288 kB/s)                                            
Selecting previously unselected package linux-image-3.16.0-62-generic.
(Reading database ... 303221 files and directories currently installed.)
Preparing to unpack .../linux-image-3.16.0-62-generic_3.16.0-62.82~14.04.1_amd64.deb ...
Done.
Unpacking linux-image-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
Selecting previously unselected package linux-image-extra-3.16.0-62-generic.
Preparing to unpack .../linux-image-extra-3.16.0-62-generic_3.16.0-62.82~14.04.1_amd64.deb ...
Unpacking linux-image-extra-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
Preparing to unpack .../linux-generic-lts-utopic_3.16.0.62.53_amd64.deb ...
Unpacking linux-generic-lts-utopic (3.16.0.62.53) over (3.16.0.60.51) ...
Preparing to unpack .../linux-image-generic-lts-utopic_3.16.0.62.53_amd64.deb ...
Unpacking linux-image-generic-lts-utopic (3.16.0.62.53) over (3.16.0.60.51) ...
Selecting previously unselected package linux-headers-3.16.0-62.
Preparing to unpack .../linux-headers-3.16.0-62_3.16.0-62.82~14.04.1_all.deb ...
Unpacking linux-headers-3.16.0-62 (3.16.0-62.82~14.04.1) ...
Selecting previously unselected package linux-headers-3.16.0-62-generic.
Preparing to unpack .../linux-headers-3.16.0-62-generic_3.16.0-62.82~14.04.1_amd64.deb ...
Unpacking linux-headers-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
Preparing to unpack .../linux-headers-generic-lts-utopic_3.16.0.62.53_amd64.deb ...
Unpacking linux-headers-generic-lts-utopic (3.16.0.62.53) over (3.16.0.60.51) ...
Setting up linux-image-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-62-generic
Found initrd image: /boot/initrd.img-3.16.0-62-generic
Found linux image: /boot/vmlinuz-3.16.0-60-generic
Found initrd image: /boot/initrd.img-3.16.0-60-generic
Found linux image: /boot/vmlinuz-3.16.0-59-generic
Found initrd image: /boot/initrd.img-3.16.0-59-generic
Found linux image: /boot/vmlinuz-3.16.0-57-generic
Found initrd image: /boot/initrd.img-3.16.0-57-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.0-62-generic
Found initrd image: /boot/initrd.img-3.16.0-62-generic
Found linux image: /boot/vmlinuz-3.16.0-60-generic
Found initrd image: /boot/initrd.img-3.16.0-60-generic
Found linux image: /boot/vmlinuz-3.16.0-59-generic
Found initrd image: /boot/initrd.img-3.16.0-59-generic
Found linux image: /boot/vmlinuz-3.16.0-57-generic
Found initrd image: /boot/initrd.img-3.16.0-57-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic-lts-utopic (3.16.0.62.53) ...
Setting up linux-headers-3.16.0-62 (3.16.0-62.82~14.04.1) ...
Setting up linux-headers-3.16.0-62-generic (3.16.0-62.82~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.0-62-generic /boot/vmlinuz-3.16.0-62-generic
Setting up linux-headers-generic-lts-utopic (3.16.0.62.53) ...
Setting up linux-generic-lts-utopic (3.16.0.62.53) ...
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.16.0-59 linux-headers-3.16.0-59-generic
  linux-image-3.16.0-59-generic linux-image-extra-3.16.0-59-generic
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  libgbm1
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by Bucky Ball on 2016-02-23
And this?

> 500 [http://ppa.launchpad.net/oibaf/gallium-nine/ubuntu/](http://ppa.launchpad.net/oibaf/gallium-nine/ubuntu/) trusty/main amd64 Packages

If you installed manually, get rid of or disable then run:

```
sudo apt-get autoremove
sudo apt-get update
```

---

### Post by Spencer_Thompson on 2016-02-23
I removed the PPA and the package isn't held back anymore. Thanks so much for the help!

---

### Post by Bucky Ball on 2016-02-23
No probs. Gotta be careful with manually installed PPAs. It looks like the two you installed, or were trying to install, their own versions of the lib file. Consequently, it had three versions in all attempting to get jammed in there when you hit 'update' perhaps. Chaos!

Glad we got there, thanks for marking as solved (I like seeing that word) and enjoy! :D

---

