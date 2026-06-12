---
title: "Trying to upgrade 12.04 LTS"
date: 2013-07-15
forum: Installation &amp; Upgrades
---

### Post by facetious on 2013-07-15
Ubuntu updates manager says there are 301 files to be downloaded - job done as far as the last file and every time I try to get it I get the following message:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.291ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.291ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]

So the upgrade/update will not proceed.

How can I get this last file - having spent 1 hour 30 mins downloading the 300 files?

---

### Post by snowpine on 2013-07-15
Hi, can you please copy & paste the output of the following terminal commands for troubleshooting purposes?

```
sudo apt-get update
sudo apt-get dist-upgrade -s
```

The -s is for "simulate" so if you are pleased with the output, then run again without the -s. :)

---

### Post by facetious on 2013-07-15
many thanks for the extremely prompt reply here are the two items requested (they mean nothing to me!!)

```
jorge@JorgeUbuntu:~$ sudo apt-get update
[sudo] password for jorge: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Get:5 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [83.5 kB]       
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [26.7 kB]   
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,383 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [296 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [4,627 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [77.4 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,186 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [311 kB] 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/main Sources                          
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [80.2 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/restricted Sources                    
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,371 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/universe Sources                      
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/restricted amd64 Packages             
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/universe TranslationIndex             
Get:22 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/main Sources [401 kB]      
Get:23 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B]
Get:24 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/universe Sources [91.6 kB] 
Get:25 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/multiverse Sources [6,582 B]
Get:26 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/main amd64 Packages [650 kB]
Get:27 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/restricted amd64 Packages [10.1 kB]
Get:28 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/universe amd64 Packages [209 kB]
Get:29 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [13.6 kB]
Get:30 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/main i386 Packages [670 kB]
Get:31 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB]
Get:32 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/universe i386 Packages [212 kB]
Get:33 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB]
Get:34 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:35 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:36 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:37 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise/universe Translation-en               
Get:38 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/main Translation-en [299 kB]
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:39 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) precise-updates/universe Translation-en [123 kB]
Fetched 3,720 kB in 1min 36s (38.6 kB/s)                                       
Reading package lists... Done
jorge@JorgeUbuntu:~$ 
```

```
64])
Inst libmuffin0 [1.1.2-0ubuntu1~precise1] (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [amd64]) []
Inst muffin-common [1.1.2-0ubuntu1~precise1] (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [all])
Inst gir1.2-muffin-3.0 [1.1.2-0ubuntu1~precise1] (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [amd64])
Inst cinnamon [1.6.7-0ubuntu1~precise1] (1.8.8-0ubuntu1~precise1 Cinnamon stable:12.04/precise [amd64]) []
Inst cinnamon-common (1.8.8-0ubuntu1~precise1 Cinnamon stable:12.04/precise [all]) []
Inst libgnome-control-center1 [1:3.4.2-0ubuntu0.9] (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [amd64]) []
Inst libgnomekbd-common [3.4.0.2-1] (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [all]) []
Inst libgnomekbd7 [3.4.0.2-1] (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst libnm-gtk-common [0.9.4.1-0ubuntu2.1] (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [all]) []
Inst dbus-x11 [1.4.18-1ubuntu1.3] (1.4.18-1ubuntu1.4 Ubuntu:12.04/precise-updates [amd64]) []
Inst libnm-gtk0 [0.9.4.1-0ubuntu2.1] (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst gnome-control-center-data [1:3.4.2-0ubuntu0.9] (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [all]) []
Inst gnome-control-center [1:3.4.2-0ubuntu0.9] (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [amd64]) []
Inst gir1.2-accountsservice-1.0 [0.6.15-2ubuntu9.4] (0.6.15-2ubuntu9.6 Ubuntu:12.04/precise-updates [amd64]) []
Inst gir1.2-gkbd-3.0 [3.4.0.2-1] (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst gir1.2-gtkclutter-1.0 (1.2.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gkbd-capplet [3.4.0.2-1] (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst cinnamon-screensaver (1.8.0-20130505194857-precise Cinnamon stable:12.04/precise [amd64])
Inst libdee-1.0-4 [1.0.10-0ubuntu1] (1.0.10-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst compiz-gnome [1:0.9.7.12-0ubuntu1] (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst compiz-plugins-default [1:0.9.7.12-0ubuntu1] (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst compiz-plugins-main-default [1:0.9.7.0~bzr19-0ubuntu10] (1:0.9.7.0~bzr19-0ubuntu10.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst compiz-core [1:0.9.7.12-0ubuntu1] (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity [5.18.0-0ubuntu2] (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst libunity-core-5.0-5 [5.18.0-0ubuntu2] (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity-services [5.18.0-0ubuntu2] (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity-common [5.18.0-0ubuntu2] (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [all]) []
Inst libdecoration0 [1:0.9.7.12-0ubuntu1] (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Inst compiz [1:0.9.7.12-0ubuntu1] (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [all])
Inst libnautilus-extension1a [1:3.4.2-0ubuntu7] (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Inst deja-dup [22.0-0ubuntu3] (22.0-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Inst dnsmasq-base [2.59-4] (2.59-4ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst firefox-globalmenu [19.0.2+build1-0ubuntu0.12.04.1] (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Inst firefox [19.0.2+build1-0ubuntu0.12.04.1] (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Inst firefox-gnome-support [19.0.2+build1-0ubuntu0.12.04.1] (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Inst firefox-locale-en [19.0.2+build1-0ubuntu0.12.04.1] (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Inst flashplugin-installer [11.2.202.275ubuntu0.12.04.1] (11.2.202.297ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst geoclue-ubuntu-geoip [0.0.2-0ubuntu6] (0.0.2-0ubuntu6.3 Ubuntu:12.04/precise-updates [amd64])
Inst gir1.2-dee-1.0 [1.0.10-0ubuntu1] (1.0.10-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst gir1.2-gjsdbus-1.0 (1.32.0-1ubuntu1 Ubuntu:12.04/precise [amd64])
Inst gir1.2-gudev-1.0 [175-0ubuntu9.2] (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Inst rhythmbox-plugin-magnatune [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst rhythmbox-plugin-cdrecorder [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst gvfs-backends [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) []
Inst gvfs-libs [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-libs:amd64 on gvfs-libs:i386] [gvfs-libs:i386 on gvfs-libs:amd64] [gvfs-libs:i386 gvfs:amd64 gvfs-daemons:amd64 ]
Inst gvfs-libs:i386 [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [i386]) [gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Inst gvfs-common [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [all]) [gvfs-bin:amd64 gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Conf gvfs-common (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [all]) [gvfs-bin:amd64 gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Conf gvfs-libs (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-bin:amd64 gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Conf gvfs-libs:i386 (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [i386]) [gvfs-bin:amd64 gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Inst gvfs-bin [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs:amd64 gvfs:i386 gvfs-daemons:amd64 ]
Inst gvfs:i386 [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [i386]) [gvfs:amd64 on gvfs:i386] [gvfs:i386 on gvfs:amd64] [gvfs:amd64 gvfs-daemons:amd64 ]
Inst gvfs [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-fuse:amd64 gvfs-daemons:amd64 ]
Inst gvfs-daemons [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-fuse:amd64 ]
Conf gvfs-daemons (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-fuse:amd64 ]
Conf gvfs:i386 (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [i386]) [gvfs-fuse:amd64 ]
Conf gvfs (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) [gvfs-fuse:amd64 ]
Inst gvfs-fuse [1.12.1-0ubuntu1.1] (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64]) []
Inst rhythmbox-plugin-zeitgeist [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [all]) []
Inst rhythmbox-data [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [all]) []
Inst rhythmbox-mozilla [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst nautilus [1:3.4.2-0ubuntu7] (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [amd64]) []
Inst nemo [1.1.2-0ubuntu1~precise1] (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [amd64]) []
Inst rhythmbox [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) [rhythmbox-plugins:amd64 ]
Inst rhythmbox-plugins [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst librhythmbox-core5 [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64]) []
Inst nautilus-data [1:3.4.2-0ubuntu7] (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [all]) []
Inst libnemo-extension1 [1.1.2-0ubuntu1~precise1] (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [amd64]) []
Inst nemo-data [1.1.2-0ubuntu1~precise1] (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [all]) []
Inst gir1.2-rb-3.0 [2.96-0ubuntu4.2] (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Inst libgck-1-0 [3.2.2-2ubuntu4] (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst libgcr-3-common [3.2.2-2ubuntu4] (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [all])
Inst libgcr-3-1 [3.2.2-2ubuntu4] (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst gnome-keyring [3.2.2-2ubuntu4] (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst gnome-screenshot [3.4.1-0ubuntu1] (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst gwibber [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64]) []
Inst gwibber-service [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Inst libgwibber2 [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Inst libgwibber-gtk2 [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Inst gwibber-service-facebook [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Inst gwibber-service-identica [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Inst gwibber-service-twitter [3.4.2-0ubuntu2.1] (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Inst libdevmapper-event1.02.1 [2:1.02.48-4ubuntu7.2] (2:1.02.48-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Inst libfs6 [2:1.0.3-1] (2:1.0.3-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst liblvm2app2.2 [2.02.66-4ubuntu7.2] (2.02.66-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Inst libneon27-gnutls [0.29.6-1] (0.29.6-1ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst libpam-gnome-keyring [3.2.2-2ubuntu4] (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Inst libraptor2-0 [2.0.6-1] (2.0.6-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst libraw5 [0.14.4-0ubuntu2] (0.14.4-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Inst unity-2d-panel [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity-2d-shell [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity-2d-spread [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64]) []
Inst unity-2d-common [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [all]) []
Inst libunity-2d-private0 [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst libxres1 [2:1.0.5-1] (2:1.0.5-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst libxvmc1 [2:1.0.6-1ubuntu2] (2:1.0.6-1ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Inst libxxf86dga1 [2:1.1.2-1] (2:1.1.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst linux-firmware [1.79.1] (1.79.4 Ubuntu:12.04/precise-updates [all])
Inst linux-generic [3.2.0.39.47] (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64]) []
Inst linux-image-generic [3.2.0.39.47] (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64]) []
Inst linux-headers-3.2.0-49 (3.2.0-49.75 Ubuntu:12.04/precise-updates [all]) []
Inst linux-headers-3.2.0-49-generic (3.2.0-49.75 Ubuntu:12.04/precise-updates [amd64]) []
Inst linux-headers-generic [3.2.0.39.47] (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64])
Inst mtools [4.0.12-1] (4.0.12-1ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst nemo-fileroller [1.0.0-20121021150425-precise] (1.8.0-20130505195020-precise Cinnamon stable:12.04/precise [amd64])
Inst network-manager-gnome [0.9.4.1-0ubuntu2.1] (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Inst plymouth-theme-ubuntu-logo [0.8.2-2ubuntu31] (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-utils [1:1.1-0ubuntu15.2] (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio [1:1.1-0ubuntu15.2] (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-module-gconf [1:1.1-0ubuntu15.2] (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-module-x11 [1:1.1-0ubuntu15.2] (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Inst python-libxml2 [2.7.8.dfsg-5.1ubuntu4.3] (2.7.8.dfsg-5.1ubuntu4.5 Ubuntu:12.04/precise-updates [amd64])
Inst samba-common-bin [2:3.6.3-2ubuntu2.4] (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Inst simple-scan [3.4.1-0ubuntu1.1] (3.4.3-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Inst ssh-askpass-gnome [1:5.9p1-5ubuntu1] (1:5.9p1-5ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst telepathy-gabble [0.16.0-0ubuntu2] (0.16.0-0ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Inst telepathy-idle [0.1.11-2] (0.1.11-2ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst thunderbird-globalmenu [17.0.4+build1-0ubuntu0.12.04.1] (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64]) []
Inst thunderbird [17.0.4+build1-0ubuntu0.12.04.1] (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64]) [thunderbird-gnome-support:amd64 ]
Inst thunderbird-gnome-support [17.0.4+build1-0ubuntu0.12.04.1] (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Inst unity-2d [5.12.0-0ubuntu1.2] (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [all])
Inst unity-lens-files [5.10.0-0ubuntu1] (5.10.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Inst unity-scope-video-remote [0.3.5-0ubuntu2.1] (0.3.5-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Inst xdiagnose [2.5.2ubuntu0.1] (2.5.3 Ubuntu:12.04/precise-updates [all])
Inst xserver-xorg-video-intel [2:2.17.0-1ubuntu4.3] (2:2.17.0-1ubuntu4.4 Ubuntu:12.04/precise-updates [amd64])
Inst xserver-xorg-video-openchrome [1:0.2.904+svn1050-1] (1:0.2.904+svn1050-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Inst pulseaudio-module-bluetooth [1:1.1-0ubuntu15.2] (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Conf perl (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf perl-modules (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [all])
Conf libperl5.14 (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf libc6-i386 (2.15-0ubuntu10.4 Ubuntu:12.04/precise-updates [amd64])
Conf libc-dev-bin (2.15-0ubuntu10.4 Ubuntu:12.04/precise-updates [amd64])
Conf linux-libc-dev (3.2.0-49.75 Ubuntu:12.04/precise-updates [amd64])
Conf libc6-dev (2.15-0ubuntu10.4 Ubuntu:12.04/precise-updates [amd64])
Conf python2.7 (2.7.3-0ubuntu3.2 Ubuntu:12.04/precise-updates [amd64])
Conf libpython2.7 (2.7.3-0ubuntu3.2 Ubuntu:12.04/precise-updates [amd64])
Conf python (2.7.3-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf bash-completion (1:1.3-1ubuntu8.1 Ubuntu:12.04/precise-updates [all])
Conf python-apt-common (0.8.3ubuntu7.1 Ubuntu:12.04/precise-updates [all])
Conf python-apt (0.8.3ubuntu7.1 Ubuntu:12.04/precise-updates [amd64])
Conf aptdaemon-data (0.43+bzr805-0ubuntu9 Ubuntu:12.04/precise-updates [all])
Conf python-aptdaemon (0.43+bzr805-0ubuntu9 Ubuntu:12.04/precise-updates [all])
Conf python-aptdaemon.gtk3widgets (0.43+bzr805-0ubuntu9 Ubuntu:12.04/precise-updates [all])
Conf python-aptdaemon.pkcompat (0.43+bzr805-0ubuntu9 Ubuntu:12.04/precise-updates [all])
Conf aptdaemon (0.43+bzr805-0ubuntu9 Ubuntu:12.04/precise-updates [all])
Conf dbus (1.4.18-1ubuntu1.4 Ubuntu:12.04/precise-updates [amd64])
Conf libaccountsservice0 (0.6.15-2ubuntu9.6 Ubuntu:12.04/precise-updates [amd64])
Conf accountsservice (0.6.15-2ubuntu9.6 Ubuntu:12.04/precise-updates [amd64])
Conf language-selector-common (0.79.3 Ubuntu:12.04/precise-updates [all])
Conf language-selector-gnome (0.79.3 Ubuntu:12.04/precise-updates [all])
Conf libcurl3-gnutls (7.22.0-3ubuntu4.2 Ubuntu:12.04/precise-updates [amd64])
Conf alsa-utils (1.0.25-1ubuntu5.2 Ubuntu:12.04/precise-updates [amd64])
Conf libcupsmime1 (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libcupscgi1 (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libcupsppdc1 (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libpoppler19 (0.18.4-1ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Conf poppler-utils (0.18.4-1ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Conf cups-common (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [all])
Conf cups-client (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf cups-bsd (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf cups-ppdc (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf cups (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libcupsdriver1 (1.5.3-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libcurl3-nss (7.22.0-3ubuntu4.2 Ubuntu:12.04/precise-updates [amd64])
Conf xserver-common (2:1.11.4-0ubuntu10.13 Ubuntu:12.04/precise-updates [all])
Conf udev (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf libdevmapper1.02.1 (2:1.02.48-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Conf dmsetup (2:1.02.48-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Conf xserver-xorg-core (2:1.11.4-0ubuntu10.13 Ubuntu:12.04/precise-updates [amd64])
Conf libgoa-1.0-common (3.4.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [all])
Conf libgoa-1.0-0 (3.4.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-online-accounts (3.4.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf mysql-common (5.5.31-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [all])
Conf libmysqlclient18:i386 (5.5.31-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [i386])
Conf libpoppler-glib8 (0.18.4-1ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Conf libwbclient0 (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf samba-common (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [all])
Conf winbind (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf libpam-winbind (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf smbclient (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf libxatracker1 (8.0.4-0ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf libxcb-dri2-0 (1.8.1-1ubuntu0.2 Ubuntu:12.04/precise-updates [amd64])
Conf libxcb-shape0 (1.8.1-1ubuntu0.2 Ubuntu:12.04/precise-updates [amd64])
Conf libplymouth2 (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Conf plymouth (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Conf plymouth-label (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Conf lightdm (1.2.3-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf linux-image-3.2.0-49-generic (3.2.0-49.75 Ubuntu:12.04/precise-updates [amd64])
Conf liblightdm-gobject-1-0 (1.2.3-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf unity-greeter (0.2.9-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf libsmbclient (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf isc-dhcp-common (4.1.ESV-R4-0ubuntu5.8 Ubuntu:12.04/precise-updates [amd64])
Conf isc-dhcp-client (4.1.ESV-R4-0ubuntu5.8 Ubuntu:12.04/precise-updates [amd64])
Conf rsyslog (5.8.6-1ubuntu8.4 Ubuntu:12.04/precise-updates [amd64])
Conf libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.6 Ubuntu:12.04/precise-updates [amd64])
Conf iptables (1.4.12-1ubuntu5 Ubuntu:12.04/precise-updates [amd64])
Conf openssh-client (1:5.9p1-5ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf openssl (1.0.1-4ubuntu5.10 Ubuntu:12.04/precise-updates [amd64])
Conf plymouth-theme-ubuntu-text (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Conf python-problem-report (2.0.1-0ubuntu17.3 Ubuntu:12.04/precise-updates [all])
Conf python-apport (2.0.1-0ubuntu17.3 Ubuntu:12.04/precise-updates [all])
Conf apport (2.0.1-0ubuntu17.3 Ubuntu:12.04/precise-updates [all])
Conf apport-gtk (2.0.1-0ubuntu17.3 Ubuntu:12.04/precise-updates [all])
Conf aptitude (0.6.6-1ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf binutils (2.22-6ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf muffin-common (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [all])
Conf libmuffin0 (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [amd64])
Conf gir1.2-muffin-3.0 (1.8.2-20130525024003-precise Cinnamon stable:12.04/precise [amd64])
Conf cinnamon-common (1.8.8-0ubuntu1~precise1 Cinnamon stable:12.04/precise [all])
Conf libgnome-control-center1 (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [amd64])
Conf libgnomekbd-common (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [all])
Conf libgnomekbd7 (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf libnm-gtk-common (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [all])
Conf dbus-x11 (1.4.18-1ubuntu1.4 Ubuntu:12.04/precise-updates [amd64])
Conf libnm-gtk0 (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-control-center-data (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [all])
Conf gnome-control-center (1:3.4.2-0ubuntu0.11 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-accountsservice-1.0 (0.6.15-2ubuntu9.6 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-gkbd-3.0 (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-gtkclutter-1.0 (1.2.0-0ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gkbd-capplet (3.4.0.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf cinnamon (1.8.8-0ubuntu1~precise1 Cinnamon stable:12.04/precise [amd64])
Conf cinnamon-screensaver (1.8.0-20130505194857-precise Cinnamon stable:12.04/precise [amd64])
Conf libdee-1.0-4 (1.0.10-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf libdecoration0 (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf compiz-core (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf compiz-plugins-default (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf compiz-gnome (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf compiz-plugins-main-default (1:0.9.7.0~bzr19-0ubuntu10.1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-services (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf libunity-core-5.0-5 (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf unity-common (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [all])
Conf compiz (1:0.9.7.12-0ubuntu2 Ubuntu:12.04/precise-updates [all])
Conf unity (5.20.0-0ubuntu2 Ubuntu:12.04/precise-updates [amd64])
Conf libnautilus-extension1a (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf deja-dup (22.0-0ubuntu4 Ubuntu:12.04/precise-updates [amd64])
Conf dnsmasq-base (2.59-4ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf firefox (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Conf firefox-globalmenu (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Conf firefox-gnome-support (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Conf firefox-locale-en (22.0+build2-0ubuntu0.12.04.2 Ubuntu:12.04/precise-updates [amd64])
Conf flashplugin-installer (11.2.202.297ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf geoclue-ubuntu-geoip (0.0.2-0ubuntu6.3 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-dee-1.0 (1.0.10-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-gjsdbus-1.0 (1.32.0-1ubuntu1 Ubuntu:12.04/precise [amd64])
Conf gir1.2-gudev-1.0 (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf librhythmbox-core5 (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox-data (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [all])
Conf gir1.2-rb-3.0 (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox-plugin-magnatune (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox-plugin-cdrecorder (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf gvfs-backends (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf gvfs-bin (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf gvfs-fuse (1.12.1-0ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf rhythmbox-plugin-zeitgeist (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [all])
Conf rhythmbox-mozilla (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf nautilus-data (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [all])
Conf nautilus (1:3.4.2-0ubuntu8 Ubuntu:12.04/precise-updates [amd64])
Conf libnemo-extension1 (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [amd64])
Conf nemo-data (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [all])
Conf nemo (1.8.4-20130709192009-precise Cinnamon stable:12.04/precise [amd64])
Conf rhythmbox-plugins (2.96-0ubuntu4.3 Ubuntu:12.04/precise-updates [amd64])
Conf libgck-1-0 (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf libgcr-3-common (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [all])
Conf libgcr-3-1 (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-keyring (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf gnome-screenshot (3.4.1-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf gwibber-service (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Conf libgwibber2 (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf libgwibber-gtk2 (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf gwibber (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [amd64])
Conf gwibber-service-facebook (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Conf gwibber-service-identica (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Conf gwibber-service-twitter (3.4.2-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Conf libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Conf libfs6 (2:1.0.3-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf liblvm2app2.2 (2.02.66-4ubuntu7.3 Ubuntu:12.04/precise-updates [amd64])
Conf libneon27-gnutls (0.29.6-1ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf libpam-gnome-keyring (3.2.2-2ubuntu4.1 Ubuntu:12.04/precise-updates [amd64])
Conf libraptor2-0 (2.0.6-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf libraw5 (0.14.4-0ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Conf libunity-2d-private0 (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-2d-common (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [all])
Conf unity-2d-panel (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-2d-shell (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-2d-spread (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf libxres1 (2:1.0.5-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf libxvmc1 (2:1.0.6-1ubuntu2.1 Ubuntu:12.04/precise-updates [amd64])
Conf libxxf86dga1 (2:1.1.2-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf linux-firmware (1.79.4 Ubuntu:12.04/precise-updates [all])
Conf linux-image-generic (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-3.2.0-49 (3.2.0-49.75 Ubuntu:12.04/precise-updates [all])
Conf linux-headers-3.2.0-49-generic (3.2.0-49.75 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-generic (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64])
Conf linux-generic (3.2.0.49.59 Ubuntu:12.04/precise-updates [amd64])
Conf mtools (4.0.12-1ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf nemo-fileroller (1.8.0-20130505195020-precise Cinnamon stable:12.04/precise [amd64])
Conf network-manager-gnome (0.9.4.1-0ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf plymouth-theme-ubuntu-logo (0.8.2-2ubuntu31.1 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-utils (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-module-gconf (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-module-x11 (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
Conf python-libxml2 (2.7.8.dfsg-5.1ubuntu4.5 Ubuntu:12.04/precise-updates [amd64])
Conf samba-common-bin (2:3.6.3-2ubuntu2.6 Ubuntu:12.04/precise-updates [amd64])
Conf simple-scan (3.4.3-0ubuntu1 Ubuntu:12.04/precise-updates [amd64])
Conf ssh-askpass-gnome (1:5.9p1-5ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf telepathy-gabble (0.16.0-0ubuntu3.1 Ubuntu:12.04/precise-updates [amd64])
Conf telepathy-idle (0.1.11-2ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf thunderbird (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf thunderbird-globalmenu (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf thunderbird-gnome-support (17.0.7+build1-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-2d (5.14.0-0ubuntu1 Ubuntu:12.04/precise-updates [all])
Conf unity-lens-files (5.10.0-0ubuntu1.1 Ubuntu:12.04/precise-updates [amd64])
Conf unity-scope-video-remote (0.3.5-0ubuntu2.2 Ubuntu:12.04/precise-updates [all])
Conf xdiagnose (2.5.3 Ubuntu:12.04/precise-updates [all])
Conf xserver-xorg-video-intel (2:2.17.0-1ubuntu4.4 Ubuntu:12.04/precise-updates [amd64])
Conf xserver-xorg-video-openchrome (1:0.2.904+svn1050-1ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf pulseaudio-module-bluetooth (1:1.1-0ubuntu15.3 Ubuntu:12.04/precise-updates [amd64])
jorge@JorgeUbuntu:~$ gksu gedit /etc/default/grub 
```

---

### Post by snowpine on 2013-07-15
I don't see any errors; do you?

If you are feeling confident, then try again without the -s for simulate. :)

---

### Post by claracc on 2013-07-16
The link: [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.291ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_11.2.202.291ubuntu0.12.04.1_amd64.deb) gives a 404 not found error since the requested package flashplugin-installer_11.2.202.291 is not in the server.

The updated and current one is 11.2.202.297 which there is in the server.

Doing ```
sudo apt-get update
``` you have updating your packages list, and now I think you are not going to find any problem

---

### Post by facetious on 2013-07-16
Many thanks folks - I used the terminal to update and all seems to have gone correctly, including using everything that was downloaded using the update manager (saving another 1 hr 30 mins of downloading again.

Obviously, the update manager and the terminal code do not work in the same way.

Thanks again.

Sorry for not putting the output in coded format - thanks for doing that.

---

