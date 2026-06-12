---
title: "Something is wrong with my Update Manager (Red Exclamation Mark)"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by sjizmc on 2012-10-18
I have some problem with my Update Manager. When I check for updates, it gives this message: 

Failed to download repository information, Check internet connection.

However, it often does have updates and will download them. 

This also comes with a couple other problems. One is a red exclamation-triangle in the bar near the top right corner that claims that some of the update information is outdated. The other is in the main Update Manager window, there is a message that says "The package information was last updated 51 days ago."


How can I fix this? I think that it is stopping my ability to update to Quetzal. Thanks!





Maybe this will help:

stevey@Stevey-U46E:~$ sudo grep -R proxy /etc/apt/*
[sudo] password for stevey: 
stevey@Stevey-U46E:~$ sudo fuser -vvv /var/lib/dpkg/lock
stevey@Stevey-U46E:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
stevey@Stevey-U46E:~$ uname -a
Linux Stevey-U46E 3.2.0-32-generic-pae #51-Ubuntu SMP Wed Sep 26 21:54:23 UTC 2012 i686 i686 i386 GNU/Linux
stevey@Stevey-U46E:~$ sudo rm /var/lib/apt/lists/lock
stevey@Stevey-U46E:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup


sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad


stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
stevey@Stevey-U46E:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
stevey@Stevey-U46E:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
stevey@Stevey-U46E:~$ sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
stevey@Stevey-U46E:~$ sudo rm -rf /var/lib/dpkg/updates/*
stevey@Stevey-U46E:~$ sudo rm -rf /var/lib/apt/lists
stevey@Stevey-U46E:~$ sudo rm /var/cache/apt/*.bin
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ 
stevey@Stevey-U46E:~$ sudo mkdir /var/lib/apt/lists
stevey@Stevey-U46E:~$ sudo mkdir /var/lib/apt/lists/partial
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get clean
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  icedtea-netx-common* libice-dev* libpthread-stubs0* libpthread-stubs0-dev*
  libsm-dev* libx11-dev* libx11-doc* libxau-dev* libxcb1-dev* libxdmcp-dev*
  libxt-dev* linux-headers-3.2.0-29* linux-headers-3.2.0-29-generic-pae*
  ttf-dejavu-extra* x11proto-core-dev* x11proto-input-dev* x11proto-kb-dev*
  xorg-sgml-doctools* xtrans-dev*
0 upgraded, 0 newly installed, 19 to remove and 0 not upgraded.
13 not fully installed or removed.
After this operation, 92.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 283711 files and directories currently installed.)
Removing icedtea-netx-common ...
Purging configuration files for icedtea-netx-common ...
Removing libxt-dev ...
Removing libsm-dev ...
Removing libice-dev ...
Removing libx11-dev ...
Removing libxcb1-dev ...
Removing libpthread-stubs0-dev ...
Removing libpthread-stubs0 ...
Removing libx11-doc ...
Removing libxau-dev ...
Removing libxdmcp-dev ...
Removing linux-headers-3.2.0-29-generic-pae ...
Removing linux-headers-3.2.0-29 ...
Removing ttf-dejavu-extra ...
Removing x11proto-input-dev ...
Removing x11proto-core-dev ...
Removing x11proto-kb-dev ...
Removing xorg-sgml-doctools ...
Removing xtrans-dev ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for fontconfig ...
Setting up libgl1-mesa-dri (8.0.4-0ubuntu0.1) ...
Setting up libglapi-mesa (8.0.4-0ubuntu0.1) ...
Setting up libgl1-mesa-glx (8.0.4-0ubuntu0.1) ...
Setting up libglu1-mesa (8.0.4-0ubuntu0.1) ...
Setting up libparted0debian1 (2.3-8ubuntu5.1) ...
Setting up libxatracker1 (8.0.4-0ubuntu0.1) ...
Setting up python-problem-report (2.0.1-0ubuntu14) ...
Setting up python-apport (2.0.1-0ubuntu14) ...
Setting up apport (2.0.1-0ubuntu14) ...
Setting up apport-gtk (2.0.1-0ubuntu14) ...
Setting up libc-dev-bin (2.15-0ubuntu10.3) ...
Setting up libc6-dev (2.15-0ubuntu10.3) ...
Setting up parted (2.3-8ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease                       
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2603 B]                        
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Get:4 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1029 B]             
Get:5 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]   
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg [198 B] 
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg [198 B]           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7078 B]           
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                   
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en                       
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                     
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]             
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release [11.9 kB]                      
Get:14 [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources [4010 B]           
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release [49.6 kB]           
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release [49.6 kB]            
Get:17 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5044 B]     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Get:19 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources [7480 B]                  
Get:20 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages [9796 B]            
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5470 B]           
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources [5019 kB]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources [155 kB]           
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages [1274 kB]          
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages [8431 B]     
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages [4796 kB]      
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]     
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex [3706 B]        
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex [2676 B]  
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex [2596 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex [2922 B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources [177 kB]         
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources [4395 B]   
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources [60.2 kB]    
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources [4745 B]   
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [410 kB]   
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [8218 B]
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [149 kB]
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [9930 B]
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3564 B]
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2605 B]
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2461 B]
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2850 B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources [2422 B]       
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources [14 B]   
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources [15.4 kB]  
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources [2669 B] 
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages [1941 B] 
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages [13.9 kB]
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages [2504 B]
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex [72 B]
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex [72 B]
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex [70 B]
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex [72 B]
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources [50.1 kB]       
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources [1950 B]  
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources [14.5 kB]   
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources [1379 B]  
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages [183 kB]  
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages [3968 B]
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages [48.7 kB]
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages [2357 B]
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex [73 B] 
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en [726 kB]          
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en [93.4 kB]   
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en [2395 B]    
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en [3341 kB]     
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en [201 kB]  
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en [5606 B]
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en [2048 B]
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [87.4 kB]
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en [1244 B]
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en [1476 B]
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en [14 B]
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en [9956 B]
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en [86.5 kB]
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en [995 B]
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en [978 B]
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en [30.3 kB]
Fetched 18.3 MB in 34s (530 kB/s)                                              
Reading package lists... Done
stevey@Stevey-U46E:~$ sudo dpkg --configure -a
stevey@Stevey-U46E:~$ sudo dpkg --clear-avail
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get --fix-missing install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stevey@Stevey-U46E:~$ LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise InRelease
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release.gpg [489 B]                     
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) precise Release [2603 B]                        
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) precise/main i386 Packages [1029 B]             
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main TranslationIndex                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security InRelease                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://linux.dropbox.com](http://linux.dropbox.com) precise/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports Release              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Sources         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Sources   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main i386 Packages   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Fetched 4121 B in 2s (1374 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
stevey@Stevey-U46E:~$ find /etc/apt -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     6	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    11	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    17	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe
    18	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    19	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    27	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise multiverse
    28	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    29	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
    37	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports main restricted universe multiverse
    38	
    39	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    40	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security main restricted
    41	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    42	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security universe
    43	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    44	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    51	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

/etc/apt/sources.list.d/google-chrome.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	# deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list.d/synapse-core-ppa-precise.list

     1	# deb [http://ppa.launchpad.net/synapse-core/ppa/ubuntu](http://ppa.launchpad.net/synapse-core/ppa/ubuntu) precise main
     2	# deb-src [http://ppa.launchpad.net/synapse-core/ppa/ubuntu](http://ppa.launchpad.net/synapse-core/ppa/ubuntu) precise main

/etc/apt/sources.list.d/elementaryart-elementary-dev-precise.list

     1	# deb [http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu](http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu) precise main
     2	# deb-src [http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu](http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu) precise main

/etc/apt/sources.list.d/google-talkplugin.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	# deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

/etc/apt/sources.list.d/dropbox.list

     1	deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main

/etc/apt/sources.list.d/zedtux-naturalscrolling-precise.list

     1	# deb [http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu](http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu) precise main
     2	# deb-src [http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu](http://ppa.launchpad.net/zedtux/naturalscrolling/ubuntu) precise main

/etc/apt/sources.list.d/webupd8team-java-precise.list

     1	# deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
     2	# deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
stevey@Stevey-U46E:~$

---

