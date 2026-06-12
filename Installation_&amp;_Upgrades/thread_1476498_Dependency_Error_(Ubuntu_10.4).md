---
title: "Dependency Error (Ubuntu 10.4)"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by trixa_13 on 2010-05-07
When I was updating my packages using the terminal:

```

trixa13@Cassiopeia®:~$ sudo apt-get update
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                                                 
Ign http://ppa.launchpad.net/cairo-dock-team/weekly/ubuntu/ lucid/main Translation-en_PH                                                                                                       
Hit http://ph.archive.ubuntu.com lucid Release.gpg                                                                                    
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_PH                                                                 
Hit http://archive.ubuntu.com lucid Release.gpg                                                                                        
Hit http://archive.canonical.com lucid Release.gpg                                                                                     
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_PH                                                                                     
Ign http://deb.playonlinux.com lucid Release.gpg                                                                                                             
Hit http://repository.glx-dock.org lucid Release.gpg                                                                                   
Ign http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/ all/main Translation-en_PH                                       
Ign http://repository.glx-dock.org/ubuntu/ lucid/cairo-dock Translation-en_PH                                                                            
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                           
Ign http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu/ lucid/main Translation-en_PH                                                                                   
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                          
Ign http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/ lucid/main Translation-en_PH                                                                                     
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                                          
Ign http://ppa.launchpad.net/docky-core/ppa/ubuntu/ lucid/main Translation-en_PH                                                                  
Hit http://ppa.launchpad.net lucid Release.gpg                                                                                                    
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_PH                                                                 
Hit http://ppa.launchpad.net lucid Release                                                                                                                              
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_PH                                                                                             
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_PH                                                                                               
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_PH                                                                                             
Hit http://ph.archive.ubuntu.com lucid-updates Release.gpg                                                                                                              
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_PH                                                                                           
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_PH                                                                                     
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_PH                                                                                       
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_PH                                                                                     
Hit http://archive.ubuntu.com lucid Release                                                                                                                                                   
Ign http://deb.playonlinux.com/ lucid/main Translation-en_PH                                                                                                            
Hit http://archive.canonical.com lucid Release                                                                                         
Hit http://repository.glx-dock.org lucid Release                                                                                       
Hit http://downloads.sourceforge.net all Release.gpg                                                                                   
Hit http://ppa.launchpad.net lucid Release                                                                       
Hit http://ppa.launchpad.net lucid Release                                                                       
Hit http://ppa.launchpad.net lucid Release                                                                                                                                       
Hit http://ppa.launchpad.net lucid Release                                                                                                                                       
Hit http://ph.archive.ubuntu.com lucid-backports Release.gpg                                                                                                                                   
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_PH                                                                                                                
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_PH                                                                                                          
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_PH                                                                                        
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_PH                                                                                      
Hit http://ph.archive.ubuntu.com lucid-security Release.gpg                                                                                                                
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_PH                                                                                             
Hit http://archive.ubuntu.com lucid/main Sources                                                                                                                           
Hit http://archive.canonical.com lucid/partner Packages                                                                                                                    
Get:1 http://deb.playonlinux.com lucid Release [1,722B]                                                                                              
Hit http://repository.glx-dock.org lucid/cairo-dock Packages                                                                                                               
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                           
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_PH                                                                                       
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_PH                               
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_PH                             
Hit http://ph.archive.ubuntu.com lucid-proposed Release.gpg                                                      
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_PH                                                   
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_PH                                                         
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_PH                                                   
Ign http://ph.archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_PH                                                     
Hit http://ph.archive.ubuntu.com lucid Release                                                                                         
Hit http://ph.archive.ubuntu.com lucid-updates Release                                                                                                       
Hit http://archive.ubuntu.com lucid/restricted Sources                                                                                                       
Hit http://archive.canonical.com lucid/partner Sources                                                                                 
Ign http://deb.playonlinux.com lucid/main Packages                                                               
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://ph.archive.ubuntu.com lucid-backports Release                                                     
Hit http://ph.archive.ubuntu.com lucid-security Release                                                      
Hit http://ph.archive.ubuntu.com lucid-proposed Release                                                                     
Hit http://ph.archive.ubuntu.com lucid/main Packages                                                                                              
Hit http://ph.archive.ubuntu.com lucid/restricted Packages                                                                  
Hit http://ph.archive.ubuntu.com lucid/restricted Sources                                                                   
Hit http://ph.archive.ubuntu.com lucid/main Sources                                                                         
Hit http://ph.archive.ubuntu.com lucid/multiverse Sources                                                                   
Ign http://deb.playonlinux.com lucid/main Packages                                                                          
Hit http://ppa.launchpad.net lucid/main Packages                                                                            
Hit http://ppa.launchpad.net lucid/main Sources                                                       
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://ppa.launchpad.net lucid/main Packages                                           
Hit http://ph.archive.ubuntu.com lucid/universe Sources                                    
Hit http://ph.archive.ubuntu.com lucid/universe Packages             
Hit http://downloads.sourceforge.net all Release                     
Hit http://ph.archive.ubuntu.com lucid/multiverse Packages           
Hit http://ph.archive.ubuntu.com lucid-updates/main Packages
Hit http://ph.archive.ubuntu.com lucid-updates/restricted Packages                       
Hit http://ph.archive.ubuntu.com lucid-updates/restricted Sources                        
Hit http://ph.archive.ubuntu.com lucid-updates/main Sources                              
Hit http://deb.playonlinux.com lucid/main Packages                                       
Hit http://ph.archive.ubuntu.com lucid-updates/multiverse Sources                        
Hit http://ph.archive.ubuntu.com lucid-updates/universe Sources    
Hit http://ph.archive.ubuntu.com lucid-updates/universe Packages
Hit http://ph.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://ph.archive.ubuntu.com lucid-backports/main Packages
Hit http://ph.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://ph.archive.ubuntu.com lucid-backports/universe Packages
Hit http://ph.archive.ubuntu.com lucid-backports/multiverse Packages
Ign http://downloads.sourceforge.net all/main Packages
Hit http://ph.archive.ubuntu.com lucid-backports/main Sources
Hit http://ph.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://ph.archive.ubuntu.com lucid-backports/universe Sources
Hit http://ph.archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://ph.archive.ubuntu.com lucid-security/main Packages
Hit http://ph.archive.ubuntu.com lucid-security/restricted Packages
Hit http://ph.archive.ubuntu.com lucid-security/restricted Sources
Ign http://downloads.sourceforge.net all/main Packages
Hit http://ph.archive.ubuntu.com lucid-security/main Sources
Hit http://ph.archive.ubuntu.com lucid-security/multiverse Sources
Hit http://ph.archive.ubuntu.com lucid-security/universe Sources
Hit http://ph.archive.ubuntu.com lucid-security/universe Packages
Hit http://ph.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://ph.archive.ubuntu.com lucid-proposed/restricted Packages
Hit http://ph.archive.ubuntu.com lucid-proposed/main Packages
Hit http://ph.archive.ubuntu.com lucid-proposed/multiverse Packages
Hit http://ph.archive.ubuntu.com lucid-proposed/universe Packages
Hit http://ph.archive.ubuntu.com lucid-proposed/restricted Sources
Hit http://ph.archive.ubuntu.com lucid-proposed/main Sources
Hit http://ph.archive.ubuntu.com lucid-proposed/multiverse Sources
Hit http://ph.archive.ubuntu.com lucid-proposed/universe Sources 
Hit http://downloads.sourceforge.net all/main Packages           
Fetched 1B in 5s (0B/s)  
Reading package lists... Done


```I got this error message:
```

trixa13@Cassiopeia®:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
44 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up liblzma1 (4.999.9beta+20091116-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liblzma1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdelibs5:
 kdelibs5 depends on liblzma1 (>= 4.999.9beta); however:
  Package liblzma1 is not configured yet.
dpkg: error processing kdelibs5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on kdelibs5 (= 4:4.4.2-0ubuntu4); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing kdelibs-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma3:
 libplasma3 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libplasma3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-runtime:
 kdebase-runtime depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 kdebase-runtime depends on libplasma3; however:
  Package libplasmNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                                      No apport report written because MaxReports is reached already
                                                                                                    No apport report written because MaxReports is reached already
                                                                                                                                                                  No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
                                                                                              No apport report written because MaxReports is reached already
                                                                                                                                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
                                                                                        No apport report written because MaxReports is reached already
                                                                                                                                                      No apport report written because MaxReports is reached already
                    No apport report written because MaxReports is reached already
                                                                                  No apport report written because MaxReports is reached already
                                                                                                                                                a3 is not configured yet.
dpkg: error processing kdebase-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-scriptengine-javascript:
 plasma-scriptengine-javascript depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 plasma-scriptengine-javascript depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 plasma-scriptengine-javascript depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing plasma-scriptengine-javascript (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdeedu4:
 libkdeedu4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libkdeedu4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of blinken:
 blinken depends No apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                                                                                                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                                                                                                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No apport report written because MaxReports is reached already
                                                                                                                                 No apport report written because MaxReports is reached already
                                                                                                                                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                                                                                                           No apport report written because MaxReports is reached already
                                                                                                                                                                                         on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 blinken depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 blinken depends on libkdeedu4 (>= 4:4.4.2); however:
  Package libkdeedu4 is not configured yet.
dpkg: error processing blinken (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepimlibs5:
 kdepimlibs5 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing kdepimlibs5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 python-kde4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 python-kde4 depends on kdepimlibs5 (>= 4:4.4.2); however:
  Package kdepimlibs5 is not configured yetNo apport report written because MaxReports is reached already
                                                                                                         No apport report written because MaxReports is reached already
                                                                                                                                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                                                                                                   .
 python-kde4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdesudo:
 kdesudo depends on kdebase-runtime (>= 4:4.3.95); however:
  Package kdebase-runtime is not configured yet.
 kdesudo depends on kdelibs5 (>= 4:4.3.95); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing kdesudo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi-kde:
 gdebi-kde depends on python-kde4 (>= 3.16.0-0ubuntu11); however:
  Package python-kde4 is not configured yet.
 gdebi-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing gdebi-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libarchive1:
 libarchive1 depends on liblzma1 (>= 4.999.9beta+20091116); however:
  Package liblzma1 is not configured yet.
dpkg: error processing libarchive1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on libarchive1 (>= 2.2.3); however:
  Package libarchive1 is not configured yet.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of install-package:
 install-package depends on gdebi-kde; however:
  Package gdebi-kde is not configured yet.
dpkg: error processing install-package (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkdecorations4:
 libkdecorations4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libkdecorations4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkwineffects1:
 libkwineffects1 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libkwineffects1 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libkwineffects1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkworkspace4:
 libkworkspace4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libkworkspace4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libkworkspace4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-window-manager:
 kde-window-manager depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 kde-window-manager depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 kde-window-manager depends on libkdecorations4 (>= 4:4.4.2); however:
  Package libkdecorations4 is not configured yet.
 kde-window-manager depends on libkwineffects1 (>= 4:4.4.2); however:
  Package libkwineffects1 is not configured yet.
 kde-window-manager depends on libkworkspace4 (>= 4:4.4.2); however:
  Package libkworkspace4 is not configured yet.
 kde-window-manager depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing kde-window-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkfontinst4:
 libkfontinst4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libkfontinst4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libkscreensaver5:
 libkscreensaver5 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libkscreensaver5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasmagenericshell4:
 libplasmagenericshell4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libplasmagenericshell4 depends on libkworkspace4 (>= 4:4.4.2); however:
  Package libkworkspace4 is not configured yet.
 libplasmagenericshell4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libplasmagenericshell4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libprocesscore4:
 libprocesscore4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libprocesscore4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libprocessui4:
 libprocessui4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libprocessui4 depends on libprocesscore4 (>= 4:4.4.2); however:
  Package libprocesscore4 is not configured yet.
dpkg: error processing libprocessui4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsolidcontrol4:
 libsolidcontrol4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libsolidcontrol4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasma-applet-system-monitor4:
 libplasma-applet-system-monitor4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libplasma-applet-system-monitor4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libplasma-applet-system-monitor4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplasmaclock4:
 libplasmaclock4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libplasmaclock4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libplasmaclock4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libksgrd4:
 libksgrd4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libksgrd4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtaskmanager4:
 libtaskmanager4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libtaskmanager4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libweather-ion4:
 libweather-ion4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 libweather-ion4 depends on libplasma3; however:
  Package libplasma3 is not configured yet.
dpkg: error processing libweather-ion4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plasma-dataengines-workspace:
 plasma-dataengines-workspace depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 plasma-dataengines-workspace depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 plasma-dataengines-workspace depends on kdepimlibs5 (>= 4:4.4.2); however:
  Package kdepimlibs5 is not configured yet.
 plasma-dataengines-workspace depends on libksgrd4 (>= 4:4.4.2); however:
  Package libksgrd4 is not configured yet.
 plasma-dataengines-workspace depends on libplasma3; however:
  Package libplasma3 is not configured yet.
 plasma-dataengines-workspace depends on libsolidcontrol4 (>= 4:4.4.2); however:
  Package libsolidcontrol4 is not configured yet.
 plasma-dataengines-workspace depends on libtaskmanager4 (>= 4:4.4.2); however:
  Package libtaskmanager4 is not configured yet.
 plasma-dataengines-workspace depends on libweather-ion4 (>= 4:4.4.2); however:
  Package libweather-ion4 is not configured yet.
dpkg: error processing plasma-dataengines-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdepim-runtime:
 kdepim-runtime depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 kdepim-runtime depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 kdepim-runtime depends on kdepimlibs5 (>= 4:4.4.2); however:
  Package kdepimlibs5 is not configured yet.
dpkg: error processing kdepim-runtime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          dpkg: dependency problems prevent configuration of plasma-widgets-workspace:
 plasma-widgets-workspace depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 plasma-widgets-workspace depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 plasma-widgets-workspace depends on libkworkspace4 (>= 4:4.4.2); however:
  Package libkworkspace4 is not configured yet.
 plasma-widgets-workspace depends on libplasma-applet-system-monitor4 (>= 4:4.4.2); however:
  Package libplasma-applet-system-monitor4 is not configured yet.
 plasma-widgets-workspace depends on libplasma3; however:
  Package libplasma3 is not configured yet.
 plasma-widgets-workspace depends on libplasmaclock4 (>= 4:4.4.2); however:
  Package libplasmaclock4 is not configured yet.
 plasma-widgets-workspace depends on libsolidcontrol4 (>= 4:4.4.2); however:
  Package libsolidcontrol4 is not configured yet.
 plasma-widgets-workspace depends on plasma-dataengines-workNo apport report written because MaxReports is reached already
                                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                                        No apport report written because MaxReports is reached already
                                                      space (= 4:4.4.2-0ubuntu14); however:
  Package plasma-dataengines-workspace is not configured yet.
 plasma-widgets-workspace depends on kdepim-runtime; however:
  Package kdepim-runtime is not configured yet.
dpkg: error processing plasma-widgets-workspace (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-data:
 kdebase-workspace-data depends on python-kde4 (>= 4:4.3.0); however:
  Package python-kde4 is not configured yet.
dpkg: error processing kdebase-workspace-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-kgreet-plugins:
 kdebase-workspace-kgreet-plugins depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 kdebase-workspace-kgreet-plugins depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing kdebase-workspace-kgreet-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of polkit-kde-1:
 polkit-kde-1 depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 polkit-kde-1 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing polkit-kde-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-bin:
 kdebase-workspace-bin depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 kdebase-workspace-bin depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 kdebase-workspace-bin depends on libkfontinst4 (>= 4:4.4.2); however:
  Package libkfontinst4 is not configured yet.
 kdebase-workspace-bin depends on libkscreensaver5 (>= 4:4.4.2); however:
  Package libkscreensaver5 is not configured yet.
 kdebase-workspace-bin depends on libkworkspace4 (>= 4:4.4.2); however:
  Package libkworkspace4 is not configured yet.
 kdebase-workspace-bin depends on libplasma3; however:
  Package libplasma3 is not configured yet.
 kdebase-workspace-bin depends on libplasmagenericshell4 (>= 4:4.4.2); however:
  Package libplasmagenericshell4 is not configured yet.
 kdebase-workspace-bin depends on libprocesscore4 (>= 4:4.4.2); however:
  Package libprocesscore4 is not cNo apport report written because MaxReports is reached already
                                                                                                onfigured yet.
 kdebase-workspace-bin depends on libprocessui4 (>= 4:4.4.2); however:
  Package libprocessui4 is not configured yet.
 kdebase-workspace-bin depends on libsolidcontrol4 (>= 4:4.4.2); however:
  Package libsolidcontrol4 is not configured yet.
 kdebase-workspace-bin depends on plasma-widgets-workspace (= 4:4.4.2-0ubuntu14); however:
  Package plasma-widgets-workspace is not configured yet.
 kdebase-workspace-bin depends on kdebase-workspace-data (= 4:4.4.2-0ubuntu14); however:
  Package kdebase-workspace-data is not configured yet.
 kdebase-workspace-bin depends on kdebase-workspace-kgreet-plugins (= 4:4.4.2-0ubuntu14); however:
  Package kdebase-workspace-kgreet-plugins is not configured yet.
 kdebase-workspace-bin depends on polkit-kde-1; however:
  Package polkit-kde-1 is not configured yet.
dpkg: error processing kdebase-workspace-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of khangman:
 khangman depends on kdeNo apport report written because MaxReports is reached already
                                                                                      No apport report written because MaxReports is reached already
                                                                                                                                                    base-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 khangman depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 khangman depends on libkdeedu4 (>= 4:4.4.2); however:
  Package libkdeedu4 is not configured yet.
dpkg: error processing khangman (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 software-properties-kde depends on install-package; however:
  Package install-package is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-kde:
 update-manager-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 update-manager-kde depends on kdesudo; however:
  Package kdesudo is No apport report written because MaxReports is reached already
                                                                                   not configured yet.
dpkg: error processing update-manager-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpackagekit:
 kpackagekit depends on kdebase-runtime (>= 4:4.3.95); however:
  Package kdebase-runtime is not configured yet.
 kpackagekit depends on kdelibs5 (>= 4:4.4.1); however:
  Package kdelibs5 is not configured yet.
 kpackagekit depends on kdebase-workspace-bin; however:
  Package kdebase-workspace-bin is not configured yet.
 kpackagekit depends on software-properties-kde; however:
  Package software-properties-kde is not configured yet.
 kpackagekit depends on update-manager-kde; however:
  Package update-manager-kde is not configured yet.
dpkg: error processing kpackagekit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kdebase-runtime (>= 4:4.4.2); however:
  Package kdebase-runtime is not configured yet.
 kubuntu-debug-installer depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
 kubuntu-debug-installer depends on kpackagekit; however:
  Package kpackagekit is not configured yet.
dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libksignalplotter4:
 libksignalplotter4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
dpkg: error processing libksignalplotter4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblsofui4:
 liblsofui4 depends on kdelibs5 (>= 4:4.4.2); however:
  Package kdelibs5 is not configured yet.
No apport report written because MaxReports is reached already
                                                              dpkg: error processing liblsofui4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 liblzma1
 kdelibs5
 kdelibs-bin
 libplasma3
 kdebase-runtime
 plasma-scriptengine-javascript
 libkdeedu4
 blinken
 kdepimlibs5
 python-kde4
 kdesudo
 gdebi-kde
 libarchive1
 gvfs-backends
 install-package
 libkdecorations4
 libkwineffects1
 libkworkspace4
 kde-window-manager
 libkfontinst4
 libkscreensaver5
 libplasmagenericshell4
 libprocesscore4
 libprocessui4
 libsolidcontrol4
 libplasma-applet-system-monitor4
 libplasmaclock4
 libksgrd4
 libtaskmanager4
 libweather-ion4
 plasma-dataengines-workspace
 kdepim-runtime
 plasma-widgets-workspace
 kdebase-workspace-data
 kdebase-workspace-kgreet-plugins
 polkit-kde-1
 kdebase-workspace-bin
 khangman
 software-properties-kde
 update-manager-kde
 kpackagekit
 kubuntu-debug-installer
 libksignalplotter4
 liblsofui4
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And it seems that I can't update the needed packages. Please help.

---

