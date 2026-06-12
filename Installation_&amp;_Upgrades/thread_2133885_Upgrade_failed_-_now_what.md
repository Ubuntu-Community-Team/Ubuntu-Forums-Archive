---
title: "Upgrade failed - now what?"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by wetzeldc on 2013-04-09
I am running 12.04 LTS
This morning the update from 3.2.0-39 to 3.2.0-40 failed.  Grub shows 3.2.0-40 but the update manager says the last update was 6 days ago.  How does one rerun/reinstall an update?

---

### Post by Laiquendi on 2013-04-09
You might have done a "partial upgrade". Problems of this type might occur when you upgrade while there are not all files uploaded or you have some dependencies problems.
Try rerunning the upgrade after some time, running *sudo apt-get install -f *or pasting here the output of *sudo apt-get upgrade* command run in terminal.

---

### Post by snowpine on 2013-04-09
Can you please copy and paste the output of the following commands?

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by wetzeldc on 2013-04-11
david@No2:~$ sudo apt-get update
[sudo] password for david: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,226 B]                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:6 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [377 kB]      
Get:13 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg [836 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:15 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,853 B]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [65.6 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [712 B]                   
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,102 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:19 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release [7,256 B]              
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [83.4 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,562 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [610 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [24.0 kB]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,389 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [249 kB] 
Get:28 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages [58.4 kB]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [196 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [73.5 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,368 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [267 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [115 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [7,834 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [114 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_US            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en               
Fetched 2,438 kB in 8s (294 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
david@No2:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bash flashplugin-installer gir1.2-dee-1.0 google-chrome-stable handbrake-gtk
  libdee-1.0-4 libgnomekbd-common libgnomekbd7 libjack-jackd2-0
  libnautilus-extension1a libnm-gtk-common libnm-gtk0 nautilus nautilus-data
  network-manager-gnome simple-scan
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.8 MB of archives.
After this operation, 304 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main google-chrome-stable i386 26.0.1410.63-r192696 [40.3 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main bash i386 4.2-2ubuntu2.1 [616 kB]
Get:3 [http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/) precise/main handbrake-gtk i386 5391svnppa1~precise1 [4,998 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libjack-jackd2-0 i386 1.9.8~dfsg.1-1ubuntu2 [170 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer i386 11.2.202.280ubuntu0.12.04.1 [7,012 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdee-1.0-4 i386 1.0.10-0ubuntu1.1 [83.3 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-dee-1.0 i386 1.0.10-0ubuntu1.1 [14.3 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomekbd-common all 3.4.0.2-1ubuntu0.1 [8,550 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomekbd7 i386 3.4.0.2-1ubuntu0.1 [54.8 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a i386 1:3.4.2-0ubuntu8 [50.9 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk-common all 0.9.4.1-0ubuntu2.2 [6,204 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk0 i386 0.9.4.1-0ubuntu2.2 [67.3 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus-data all 1:3.4.2-0ubuntu8 [63.4 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus i386 1:3.4.2-0ubuntu8 [845 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main network-manager-gnome i386 0.9.4.1-0ubuntu2.2 [402 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main simple-scan i386 3.4.3-0ubuntu1 [117 kB]
Fetched 47.8 MB in 20s (2,339 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 620459 files and directories currently installed.)
Preparing to replace bash 4.2-2ubuntu2 (using .../bash_4.2-2ubuntu2.1_i386.deb) ...
Unpacking replacement bash ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up bash (4.2-2ubuntu2.1) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
Processing triggers for menu ...
(Reading database ... 620459 files and directories currently installed.)
Preparing to replace google-chrome-stable 26.0.1410.43-r189671 (using .../google-chrome-stable_26.0.1410.63-r192696_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace libjack-jackd2-0 1.9.8~dfsg.1-1ubuntu1 (using .../libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb) ...
Unpacking replacement libjack-jackd2-0 ...
Preparing to replace flashplugin-installer 11.2.202.275ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.280ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace libdee-1.0-4 1.0.10-0ubuntu1 (using .../libdee-1.0-4_1.0.10-0ubuntu1.1_i386.deb) ...
Unpacking replacement libdee-1.0-4 ...
Preparing to replace gir1.2-dee-1.0 1.0.10-0ubuntu1 (using .../gir1.2-dee-1.0_1.0.10-0ubuntu1.1_i386.deb) ...
Unpacking replacement gir1.2-dee-1.0 ...
Preparing to replace handbrake-gtk 5385svnppa1~precise1 (using .../handbrake-gtk_5391svnppa1~precise1_i386.deb) ...
Unpacking replacement handbrake-gtk ...
Preparing to replace libgnomekbd-common 3.4.0.2-1 (using .../libgnomekbd-common_3.4.0.2-1ubuntu0.1_all.deb) ...
Unpacking replacement libgnomekbd-common ...
Preparing to replace libgnomekbd7 3.4.0.2-1 (using .../libgnomekbd7_3.4.0.2-1ubuntu0.1_i386.deb) ...
Unpacking replacement libgnomekbd7 ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu7 (using .../libnautilus-extension1a_1%3a3.4.2-0ubuntu8_i386.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace libnm-gtk-common 0.9.4.1-0ubuntu2.1 (using .../libnm-gtk-common_0.9.4.1-0ubuntu2.2_all.deb) ...
Unpacking replacement libnm-gtk-common ...
Preparing to replace libnm-gtk0 0.9.4.1-0ubuntu2.1 (using .../libnm-gtk0_0.9.4.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement libnm-gtk0 ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu7 (using .../nautilus-data_1%3a3.4.2-0ubuntu8_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu7 (using .../nautilus_1%3a3.4.2-0ubuntu8_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace network-manager-gnome 0.9.4.1-0ubuntu2.1 (using .../network-manager-gnome_0.9.4.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Preparing to replace simple-scan 3.4.1-0ubuntu1.1 (using .../simple-scan_3.4.3-0ubuntu1_i386.deb) ...
Unpacking replacement simple-scan ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz)
Installing from local file /tmp/tmpJUQB6P.gz
Flash Plugin installed.
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Setting up google-chrome-stable (26.0.1410.63-r192696) ...
Setting up libjack-jackd2-0 (1.9.8~dfsg.1-1ubuntu2) ...
Setting up flashplugin-installer (11.2.202.280ubuntu0.12.04.1) ...
Setting up libdee-1.0-4 (1.0.10-0ubuntu1.1) ...
Setting up gir1.2-dee-1.0 (1.0.10-0ubuntu1.1) ...
Setting up handbrake-gtk (5391svnppa1~precise1) ...
Setting up libgnomekbd-common (3.4.0.2-1ubuntu0.1) ...
Setting up libgnomekbd7 (3.4.0.2-1ubuntu0.1) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu8) ...
Setting up libnm-gtk-common (0.9.4.1-0ubuntu2.2) ...
Setting up libnm-gtk0 (0.9.4.1-0ubuntu2.2) ...
Setting up nautilus-data (1:3.4.2-0ubuntu8) ...
Setting up nautilus (1:3.4.2-0ubuntu8) ...
Setting up network-manager-gnome (0.9.4.1-0ubuntu2.2) ...
Setting up simple-scan (3.4.3-0ubuntu1) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@No2:~$

---

### Post by wetzeldc on 2013-04-12
david@No2:~$ sudo apt-get update
[sudo] password for david: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,226 B]                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:6 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:9 [http://archive.canonical.com](http://archive.canonical.com) precise Release [7,078 B]                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [377 kB]      
Get:13 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg [836 B]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Get:15 [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages [5,853 B]    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [65.6 kB]      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [712 B]                   
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [1,102 B]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:19 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release [7,256 B]              
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [83.4 kB] 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [6,562 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [610 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [24.0 kB]  
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,389 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [249 kB] 
Get:28 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps i386 Packages [58.4 kB]   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [196 kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [73.5 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,368 B]
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:41 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [267 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [115 kB]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [7,834 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [114 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [1,253 B]
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en_US            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps Translation-en               
Fetched 2,438 kB in 8s (294 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/u...source/Sources]("http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/aheck/ppa/u...-i386/Packages]("http://ppa.launchpad.net/aheck/ppa/ubuntu/dists/precise/main/binary-i386/Packages")  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
david@No2:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  bash flashplugin-installer gir1.2-dee-1.0 google-chrome-stable handbrake-gtk
  libdee-1.0-4 libgnomekbd-common libgnomekbd7 libjack-jackd2-0
  libnautilus-extension1a libnm-gtk-common libnm-gtk0 nautilus nautilus-data
  network-manager-gnome simple-scan
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.8 MB of archives.
After this operation, 304 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main google-chrome-stable i386 26.0.1410.63-r192696 [40.3 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main bash i386 4.2-2ubuntu2.1 [616 kB]
Get:3 [http://ppa.launchpad.net/stebbins/ha...pshots/ubuntu/]("http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu/") precise/main handbrake-gtk i386 5391svnppa1~precise1 [4,998 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libjack-jackd2-0 i386 1.9.8~dfsg.1-1ubuntu2 [170 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse flashplugin-installer i386 11.2.202.280ubuntu0.12.04.1 [7,012 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libdee-1.0-4 i386 1.0.10-0ubuntu1.1 [83.3 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main gir1.2-dee-1.0 i386 1.0.10-0ubuntu1.1 [14.3 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomekbd-common all 3.4.0.2-1ubuntu0.1 [8,550 B]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libgnomekbd7 i386 3.4.0.2-1ubuntu0.1 [54.8 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnautilus-extension1a i386 1:3.4.2-0ubuntu8 [50.9 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk-common all 0.9.4.1-0ubuntu2.2 [6,204 B]
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libnm-gtk0 i386 0.9.4.1-0ubuntu2.2 [67.3 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus-data all 1:3.4.2-0ubuntu8 [63.4 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main nautilus i386 1:3.4.2-0ubuntu8 [845 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main network-manager-gnome i386 0.9.4.1-0ubuntu2.2 [402 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main simple-scan i386 3.4.3-0ubuntu1 [117 kB]
Fetched 47.8 MB in 20s (2,339 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 620459 files and directories currently installed.)
Preparing to replace bash 4.2-2ubuntu2 (using .../bash_4.2-2ubuntu2.1_i386.deb) ...
Unpacking replacement bash ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up bash (4.2-2ubuntu2.1) ...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to  provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
Processing triggers for menu ...
(Reading database ... 620459 files and directories currently installed.)
Preparing to replace google-chrome-stable 26.0.1410.43-r189671 (using  .../google-chrome-stable_26.0.1410.63-r192696_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace libjack-jackd2-0 1.9.8~dfsg.1-1ubuntu1 (using .../libjack-jackd2-0_1.9.8~dfsg.1-1ubuntu2_i386.deb) ...
Unpacking replacement libjack-jackd2-0 ...
Preparing to replace flashplugin-installer 11.2.202.275ubuntu0.12.04.1  (using .../flashplugin-installer_11.2.202.280ubuntu0.12.04.1_i386.deb)  ...
Unpacking replacement flashplugin-installer ...
Preparing to replace libdee-1.0-4 1.0.10-0ubuntu1 (using .../libdee-1.0-4_1.0.10-0ubuntu1.1_i386.deb) ...
Unpacking replacement libdee-1.0-4 ...
Preparing to replace gir1.2-dee-1.0 1.0.10-0ubuntu1 (using .../gir1.2-dee-1.0_1.0.10-0ubuntu1.1_i386.deb) ...
Unpacking replacement gir1.2-dee-1.0 ...
Preparing to replace handbrake-gtk 5385svnppa1~precise1 (using .../handbrake-gtk_5391svnppa1~precise1_i386.deb) ...
Unpacking replacement handbrake-gtk ...
Preparing to replace libgnomekbd-common 3.4.0.2-1 (using .../libgnomekbd-common_3.4.0.2-1ubuntu0.1_all.deb) ...
Unpacking replacement libgnomekbd-common ...
Preparing to replace libgnomekbd7 3.4.0.2-1 (using .../libgnomekbd7_3.4.0.2-1ubuntu0.1_i386.deb) ...
Unpacking replacement libgnomekbd7 ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu7 (using  .../libnautilus-extension1a_1%3a3.4.2-0ubuntu8_i386.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace libnm-gtk-common 0.9.4.1-0ubuntu2.1 (using .../libnm-gtk-common_0.9.4.1-0ubuntu2.2_all.deb) ...
Unpacking replacement libnm-gtk-common ...
Preparing to replace libnm-gtk0 0.9.4.1-0ubuntu2.1 (using .../libnm-gtk0_0.9.4.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement libnm-gtk0 ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu7 (using .../nautilus-data_1%3a3.4.2-0ubuntu8_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace nautilus 1:3.4.2-0ubuntu7 (using .../nautilus_1%3a3.4.2-0ubuntu8_i386.deb) ...
Unpacking replacement nautilus ...
Preparing to replace network-manager-gnome 0.9.4.1-0ubuntu2.1 (using .../network-manager-gnome_0.9.4.1-0ubuntu2.2_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Preparing to replace simple-scan 3.4.1-0ubuntu1.1 (using .../simple-scan_3.4.3-0ubuntu1_i386.deb) ...
Unpacking replacement simple-scan ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading [http://archive.canonical.com/pool/pa...80.orig.tar.gz]("http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz")
Installing from local file /tmp/tmpJUQB6P.gz
Flash Plugin installed.
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for libglib2.0-0 ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Setting up google-chrome-stable (26.0.1410.63-r192696) ...
Setting up libjack-jackd2-0 (1.9.8~dfsg.1-1ubuntu2) ...
Setting up flashplugin-installer (11.2.202.280ubuntu0.12.04.1) ...
Setting up libdee-1.0-4 (1.0.10-0ubuntu1.1) ...
Setting up gir1.2-dee-1.0 (1.0.10-0ubuntu1.1) ...
Setting up handbrake-gtk (5391svnppa1~precise1) ...
Setting up libgnomekbd-common (3.4.0.2-1ubuntu0.1) ...
Setting up libgnomekbd7 (3.4.0.2-1ubuntu0.1) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu8) ...
Setting up libnm-gtk-common (0.9.4.1-0ubuntu2.2) ...
Setting up libnm-gtk0 (0.9.4.1-0ubuntu2.2) ...
Setting up nautilus-data (1:3.4.2-0ubuntu8) ...
Setting up nautilus (1:3.4.2-0ubuntu8) ...
Setting up network-manager-gnome (0.9.4.1-0ubuntu2.2) ...
Setting up simple-scan (3.4.3-0ubuntu1) ...
Processing triggers for menu ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
david@No2:~$

---

### Post by kafkaian on 2013-04-14
Are you sure it isn't the Sandybridge regression failure

[https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/precise/+source/linux/+bug/1140716)

---

