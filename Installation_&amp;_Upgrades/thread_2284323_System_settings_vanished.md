---
title: "System settings vanished"
date: 2015-06-28
forum: Installation &amp; Upgrades
---

### Post by nag92 on 2015-06-28
I do not know what happened, I am new to Ubuntu. I am missing the "system setting" application. I tried to run this.

```
 sudo apt-get install unity-control-center
```


and get the following output.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: indicator-sound but it is not going to be installed
                        Recommends: libcanberra-pulse but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Can someplease help me. I have searched around, but nothing I found fix the problem.

---

### Post by deadflowr on 2015-06-28
What does it say if you run
```
sudo apt-get update
```
and then run
```
sudo apt-get dist-upgrade
```
you can abort the second command if you want. (press N)
either way, post the full output of what it says.

---

### Post by nag92 on 2015-06-28
After running```
 sudo apt-get update
``` I get 
```
Ign http://dl.google.com stable InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://dl.google.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security Release                         
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com trusty-updates Release.gpg                    
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages       
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://dl.google.com stable/main amd64 Packages                            
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://us.archive.ubuntu.com trusty-updates Release                        
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://dl.google.com stable/main i386 Packages                             
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://security.ubuntu.com trusty-security/multiverse amd64 Packages       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://packages.ros.org trusty InRelease                                   
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://packages.ros.org trusty/main amd64 Packages                         
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://packages.ros.org trusty/main i386 Packages                          
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages              
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign http://packages.ros.org trusty/main Translation-en_US                      
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Ign http://packages.ros.org trusty/main Translation-en                         
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Hit http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://ppa.launchpad.net trusty/main Translation-en             
Hit http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com trusty-updates/main i386 Packages             
Hit http://ppa.launchpad.net trusty/main amd64 Packages            
Hit http://us.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://ppa.launchpad.net trusty/main i386 Packages             
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Reading package lists... Done                      
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://dl.google.com/linux/chrome/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


```

After  ```
 sudo apt-get dist-upgrade
``` I got 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apg cups-pk-helper gir1.2-rb-3.0 gir1.2-secret-1 gkbd-capplet
  gnome-control-center-shared-data gnome-menus gstreamer0.10-pulseaudio
  libdmapsharing-3.0-2 libfftw3-single3 libgnomekbd-common libgnomekbd8
  libgpod-common libgpod4 libmbim-glib0 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libpulsedsp libqmi-glib0 libqt5webkit5-qmlwebkitplugin
  librhythmbox-core8 libsgutils2-2 libtimezonemap1 libufe-xidgetter0
  linux-sound-base media-player-info pulseaudio-utils python3-mako
  python3-markupsafe qtdeclarative5-accounts-plugin
  qtdeclarative5-dialogs-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets rhythmbox-data rtkit
  signon-keyring-extension ubuntu-system-service unity-webapps-qml
  usb-modeswitch usb-modeswitch-data
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  apparmor-easyprof libpq-dev libpq5 nfs-common nfs-kernel-server
  python-pkg-resources python-setuptools python-six python3-apparmor
  python3-libapparmor python3-pkg-resources python3-six rpcbind
  xserver-xorg-video-intel-lts-utopic
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,620 kB of archives.
After this operation, 8,192 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpq-dev amd64 9.3.9-0ubuntu0.14.04 [140 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpq5 amd64 9.3.9-0ubuntu0.14.04 [81.4 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nfs-common amd64 1:1.2.8-6ubuntu1.1 [182 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nfs-kernel-server amd64 1:1.2.8-6ubuntu1.1 [85.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main rpcbind amd64 0.2.1-2ubuntu2.1 [37.0 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-setuptools all 3.3-1ubuntu2 [230 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-pkg-resources all 3.3-1ubuntu2 [61.9 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python-six all 1.5.2-1ubuntu1 [8,238 B]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-pkg-resources all 3.3-1ubuntu2 [31.7 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-six all 1.5.2-1ubuntu1 [8,310 B]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main xserver-xorg-video-intel-lts-utopic amd64 2:2.99.914-1~exp1ubuntu4.3~trusty1 [657 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-libapparmor amd64 2.8.95~2430-0ubuntu5.2 [23.4 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apparmor amd64 2.8.95~2430-0ubuntu5.2 [63.8 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main apparmor-easyprof all 2.8.95~2430-0ubuntu5.2 [10.1 kB]
Fetched 1,620 kB in 1s (1,486 kB/s)            
(Reading database ... 273833 files and directories currently installed.)
Preparing to unpack .../libpq-dev_9.3.9-0ubuntu0.14.04_amd64.deb ...
Unpacking libpq-dev (9.3.9-0ubuntu0.14.04) over (9.3.8-0ubuntu0.4.04) ...
Preparing to unpack .../libpq5_9.3.9-0ubuntu0.14.04_amd64.deb ...
Unpacking libpq5 (9.3.9-0ubuntu0.14.04) over (9.3.8-0ubuntu0.4.04) ...
Preparing to unpack .../nfs-common_1%3a1.2.8-6ubuntu1.1_amd64.deb ...
Unpacking nfs-common (1:1.2.8-6ubuntu1.1) over (1:1.2.8-6ubuntu1) ...
Preparing to unpack .../nfs-kernel-server_1%3a1.2.8-6ubuntu1.1_amd64.deb ...
Unpacking nfs-kernel-server (1:1.2.8-6ubuntu1.1) over (1:1.2.8-6ubuntu1) ...
Preparing to unpack .../rpcbind_0.2.1-2ubuntu2.1_amd64.deb ...
rpcbind stop/waiting
Unpacking rpcbind (0.2.1-2ubuntu2.1) over (0.2.1-2ubuntu1) ...
Preparing to unpack .../python-setuptools_3.3-1ubuntu2_all.deb ...
Unpacking python-setuptools (3.3-1ubuntu2) over (3.3-1ubuntu1) ...
Preparing to unpack .../python-pkg-resources_3.3-1ubuntu2_all.deb ...
Unpacking python-pkg-resources (3.3-1ubuntu2) over (3.3-1ubuntu1) ...
Preparing to unpack .../python-six_1.5.2-1ubuntu1_all.deb ...
Unpacking python-six (1.5.2-1ubuntu1) over (1.5.2-1) ...
Preparing to unpack .../python3-pkg-resources_3.3-1ubuntu2_all.deb ...
Unpacking python3-pkg-resources (3.3-1ubuntu2) over (3.3-1ubuntu1) ...
Preparing to unpack .../python3-six_1.5.2-1ubuntu1_all.deb ...
Unpacking python3-six (1.5.2-1ubuntu1) over (1.5.2-1) ...
Preparing to unpack .../xserver-xorg-video-intel-lts-utopic_2%3a2.99.914-1~exp1ubuntu4.3~trusty1_amd64.deb ...
Unpacking xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.3~trusty1) over (2:2.99.914-1~exp1ubuntu4.2~trusty1) ...
Preparing to unpack .../python3-libapparmor_2.8.95~2430-0ubuntu5.2_amd64.deb ...
Unpacking python3-libapparmor (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ...
Preparing to unpack .../python3-apparmor_2.8.95~2430-0ubuntu5.2_amd64.deb ...
Unpacking python3-apparmor (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ...
Preparing to unpack .../apparmor-easyprof_2.8.95~2430-0ubuntu5.2_all.deb ...
Unpacking apparmor-easyprof (2.8.95~2430-0ubuntu5.2) over (2.8.95~2430-0ubuntu5.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Setting up libpq5 (9.3.9-0ubuntu0.14.04) ...
Setting up libpq-dev (9.3.9-0ubuntu0.14.04) ...
Setting up rpcbind (0.2.1-2ubuntu2.1) ...
rpcbind start/running, process 15344
Setting up nfs-common (1:1.2.8-6ubuntu1.1) ...
statd stop/waiting
statd start/running, process 15544
gssd stop/pre-start, process 15578
idmapd stop/waiting
idmapd start/running, process 15629
Setting up nfs-kernel-server (1:1.2.8-6ubuntu1.1) ...
 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Not starting NFS kernel daemon: no exports.
Setting up python-pkg-resources (3.3-1ubuntu2) ...
Setting up python-setuptools (3.3-1ubuntu2) ...
Setting up python-six (1.5.2-1ubuntu1) ...
Setting up python3-pkg-resources (3.3-1ubuntu2) ...
Setting up python3-six (1.5.2-1ubuntu1) ...
Setting up xserver-xorg-video-intel-lts-utopic (2:2.99.914-1~exp1ubuntu4.3~trusty1) ...
Setting up python3-libapparmor (2.8.95~2430-0ubuntu5.2) ...
Setting up python3-apparmor (2.8.95~2430-0ubuntu5.2) ...
Setting up apparmor-easyprof (2.8.95~2430-0ubuntu5.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...



```

I was then able to install the unity control center, thank you!

---

