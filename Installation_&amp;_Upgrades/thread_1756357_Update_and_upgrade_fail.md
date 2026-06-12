---
title: "Update and upgrade fail"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by markhorrocks on 2011-05-12
I have recently installed a fresh copy of Natty and now get this error on update


sudo apt-get update
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick InRelease                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg [489 B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty InRelease                               
Get:2 [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release [2,605 B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:3 [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main amd64 Packages [781 B]            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main TranslationIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [23.2 kB]              
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease [7,092 B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Get:7 [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg [198 B]                   
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates InRelease                       
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [5,941 B]         
Get:9 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Get:10 [http://archive.canonical.com](http://archive.canonical.com) natty Release [5,916 B]                    
Get:11 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty Release.gpg [198 B]                  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                        
Get:14 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free amd64 Packages [3,257 B]       
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [2,151 B]    
Get:17 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates Release.gpg [198 B]          
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [14 B]     
Get:19 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Get:20 [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources [4,124 B]            
Get:21 [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free amd64 Packages [6,104 B]   
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages [20.6 kB] 
Get:23 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Get:24 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]                      
Get:25 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty Release [39.8 kB]                    
Get:26 [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages [6,733 B]     
Get:27 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages [14 B]               
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                      
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,772 B]                        
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages [9,483 B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free TranslationIndex                  
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages [14 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en_PH                   
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,741 B]                        
Get:34 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates Release [27.2 kB]            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main Translation-en                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Get:35 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,773 B]                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free TranslationIndex              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                                     
Get:36 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/main Sources [862 kB]                
Get:37 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [6,994 B]                   
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex [636 B]            
Get:39 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [593 B]                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_PH                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,161 B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_PH               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources/DiffIndex                      
Get:41 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/restricted Sources [4,104 B]         
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages/DiffIndex [1,085 B]  
Get:43 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/universe Sources [4,380 kB]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_PH [1,575 B]         
Get:45 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en [2,408 B]            
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en [33.9 kB]            
44% [46 Translation-en bzip2 0 B] [43 Sources 1,330 kB/4,380 kB 30%] [Waiting fbzip2: (stdin) is not a bzip2 file.
Get:47 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages [844 B]              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en_PH                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/free Translation-en                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en_PH             
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) natty/non-free Translation-en                
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages                         
  404  Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_PH           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Get:48 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                         
Get:49 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                           
Get:50 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:51 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,076 B]               
Get:52 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/main amd64 Packages [1,550 kB]       
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_PH     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_PH     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_PH       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:53 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/restricted amd64 Packages [9,001 B]  
Get:54 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/universe amd64 Packages [6,004 kB]   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_PH                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:55 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/multiverse amd64 Packages [181 kB]
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/universe TranslationIndex               
Get:56 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/main Sources [22.4 kB]       
Get:57 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:58 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/universe Sources [6,905 B]   
Get:59 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/multiverse Sources [980 B]   
Get:60 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/main amd64 Packages [83.0 kB]
Get:61 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,395 B]                   
Get:62 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main amd64 Packages [2,162 B]            
Get:63 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/restricted amd64 Packages [14 B]
Get:64 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/universe amd64 Packages [29.1 kB]
Get:65 [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/multiverse amd64 Packages [2,191 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_PH                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_PH                      
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_PH                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/main Translation-en_PH                  
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/main Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty/universe Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 8,264 kB in 2min 7s (64.9 kB/s)
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_pitti_postgresql_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/pitti/postgresql/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/pitti/postgresql/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/main/binary-amd64/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/natty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-on-rails_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-on-rails_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
mark@Inspiron-1564:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  app-install-data evince evince-common file-roller gir1.2-panelapplet-3.0
  gnome-panel gnome-panel-bonobo gnome-panel-data gnome-session
  gnome-session-bin gnome-session-common gnome-user-guide google-chrome-stable
  gwibber gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter language-selector-common language-selector-gnome
  libevdocument3 libevview3 libnux-0.9-0 libnux-0.9-common
  liboverlay-scrollbar-0.1-0 libpanel-applet-3-0 libpanel-applet2-0
  libplymouth2 libpoppler-glib6 libpq-dev libpq5 libpulse-browse0
  libpulse-mainloop-glib0 libpulse0 nux-tools overlay-scrollbar plymouth
  plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text
  poppler-utils postgresql-client-common postgresql-common pulseaudio
  pulseaudio-esound-compat pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils python-glade2 python-gtk2
  samba-common-bin skype software-center ubuntu-docs ubuntu-sso-client
  update-manager update-manager-core winetricks
59 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly

---

### Post by markhorrocks on 2011-05-12
bump. This is a serious bug. I can't update anything. Google turns up nothing on the last error message.

---

### Post by markhorrocks on 2011-05-13
I used tweak to get rid of the offending repositories. No more unofficial repositories for me.

---

