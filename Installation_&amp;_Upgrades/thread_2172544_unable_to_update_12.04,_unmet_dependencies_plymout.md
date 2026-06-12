---
title: "unable to update 12.04, unmet dependencies plymouth?"
date: 2013-09-05
forum: Installation &amp; Upgrades
---

### Post by d-a-cousins on 2013-09-05
Hi
 I have recently updated 12.04, having not done so for a few months (for various reasons). The update did not complete properly (we get powercuts where I live) and now my system is suboptimal: most immediately, I've returned to getting a splash screen, the wireless wlan0 is not recognized (so I have to solve this connected at work BST 9-5) and updates are not completing. I'm far from savvy with fixes - is the problem with the libplymouth2 version and if so, how do I rectify it? Any help would be greatly appreciated.

 

 **sudo apt-get update**

 ```
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
 Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                      
 Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                      
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                            
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg          
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release.gpg         
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                      
 Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]             
 Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]              
 Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                          
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                    
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release                        
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security Release                       
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                   
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages           
 Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [8,596 B]           
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages          
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
 Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [5,938 B]
 Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [5,938 B]
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
 Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [26.2 kB]                   
 Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [16.2 kB]           
 Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [16.2 kB]            
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex              
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                       
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                        
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages           
 Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages            
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                   
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                         
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                  
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                   
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                               
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                           
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                         
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages                    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages               
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex         
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources                   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Sources                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Sources            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Sources              
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB              
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Sources            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main amd64 Packages           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted amd64 Packages     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe amd64 Packages       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse amd64 Packages     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main i386 Packages            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted i386 Packages      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe i386 Packages        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse i386 Packages
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main TranslationIndex
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse TranslationIndex   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted TranslationIndex   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe TranslationIndex     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB         
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en            
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en      
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_GB              
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                     
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/main Translation-en           
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/multiverse Translation-en     
 Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/restricted Translation-en
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-security/universe Translation-en
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB            
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
 Fetched 103 kB in 0s (363 kB/s)
 Error org.freedesktop.DBus.Error.Spawn.PermissionsInvalid: The permission of the setuid helper is not correct
 Reading package lists... Done
```
 

 ______________________________________________________________________________________
 

 **sudo dpkg --configure -a**

 [sudo] password for teamlithium:  

```
 dpkg: dependency problems prevent configuration of plymouth-x11:
  plymouth-x11 depends on libplymouth2 (= 0.8.2-2ubuntu31); however:
   Version of libplymouth2 on system is 0.8.2-2ubuntu31.1.
  plymouth-x11 depends on plymouth (= 0.8.2-2ubuntu31); however:
   Package plymouth is not configured yet.
 dpkg: error processing plymouth-x11 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of mountall:
  mountall depends on plymouth; however:
   Package plymouth is not configured yet.
 dpkg: error processing mountall (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-logo:
  plymouth-theme-ubuntu-logo depends on plymouth; however:
   Package plymouth is not configured yet.
 dpkg: error processing plymouth-theme-ubuntu-logo (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
  plymouth-theme-ubuntu-text depends on plymouth; however:
   Package plymouth is not configured yet.
 dpkg: error processing plymouth-theme-ubuntu-text (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of plymouth-label:
  plymouth-label depends on libplymouth2 (= 0.8.2-2ubuntu31); however:
   Version of libplymouth2 on system is 0.8.2-2ubuntu31.1.
  plymouth-label depends on plymouth (= 0.8.2-2ubuntu31); however:
   Package plymouth is not configured yet.
 dpkg: error processing plymouth-label (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of upstart:
  upstart depends on mountall; however:
   Package mountall is not configured yet.
 dpkg: error processing upstart (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of alsa-utils:
  alsa-utils depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing alsa-utils (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of lightdm:
  lightdm depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing lightdm (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of network-manager:
  network-manager depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing network-manager (--configure):
  dependency problems - leaving unconfigured
 Setting up tex-common (2.10) ...
 Running mktexlsr. This may take some time... done.
 texlive-base is not ready, delaying updmap-sys call
 texlive-base is not ready, skipping fmtutil-sys --all call
 dpkg: dependency problems prevent configuration of udev:
  udev depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
  udev depends on upstart (>= 1.4-0ubuntu6); however:
   Package upstart is not configured yet.
 dpkg: error processing udev (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of xdiagnose:
  xdiagnose depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing xdiagnose (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of ubuntu-minimal:
  ubuntu-minimal depends on udev; however:
   Package udev is not configured yet.
  ubuntu-minimal depends on upstart; however:
   Package upstart is not configured yet.
 dpkg: error processing ubuntu-minimal (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of rsyslog:
  rsyslog depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing rsyslog (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of network-manager-gnome:
  network-manager-gnome depends on network-manager (>= 0.9.4); however:
   Package network-manager is not configured yet.
 dpkg: error processing network-manager-gnome (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of apport:
  apport depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing apport (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of cups:
  cups depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing cups (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of gdm:
  gdm depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
  gdm depends on udev (>= 166-0ubuntu4); however:
   Package udev is not configured yet.
 dpkg: error processing gdm (--configure):
  dependency problems - leaving unconfigured
 Setting up texlive-base (2009-15) ...
 mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVE...  
 mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN...  
 mktexlsr: Updating /var/lib/texmf/ls-R...  
 mktexlsr: Done.
 Running mktexlsr. This may take some time... done.
 Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-base.cnf.
     This may take some time...  
 fmtutil-sys failed. Output has been stored in
 /tmp/fmtutil.MJ55ONye
 Please include this file if you report a bug.
 

 dpkg: error processing texlive-base (--configure):
  subprocess installed post-installation script returned error exit status 1
 dpkg: dependency problems prevent configuration of texlive-luatex:
  texlive-luatex depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-luatex (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-generic-recommended:
  texlive-generic-recommended depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-generic-recommended (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
  texlive-fonts-recommended depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-fonts-recommended (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-pictures:
  texlive-pictures depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-pictures (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of apport-gtk:
  apport-gtk depends on apport (>= 0.41); however:
   Package apport is not configured yet.
 dpkg: error processing apport-gtk (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-fonts-extra:
  texlive-fonts-extra depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-fonts-extra (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of context:
  context depends on texlive-base (>= 2009); however:
   Package texlive-base is not configured yet.
 dpkg: error processing context (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of xserver-xorg-core:
  xserver-xorg-core depends on udev (>= 149); however:
   Package udev is not configured yet.
 dpkg: error processing xserver-xorg-core (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
  xserver-xorg-video-openchrome depends on xorg-video-abi-11; however:
   Package xorg-video-abi-11 is not installed.
   Package xserver-xorg-core which provides xorg-video-abi-11 is not configured yet.
  xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.10.99.901); however:
   Package xserver-xorg-core is not configured yet.
 dpkg: error processing xserver-xorg-video-openchrome (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of dbus:
  dbus depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
  dbus depends on upstart (>= 0.6.3-6); however:
   Package upstart is not configured yet.
 dpkg: error processing dbus (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of rhythmbox:
  rhythmbox depends on dbus; however:
   Package dbus is not configured yet.
 dpkg: error processing rhythmbox (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-formats-extra:
  texlive-formats-extra depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-formats-extra (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libsolid4:
  libsolid4 depends on udev; however:
   Package udev is not configured yet.
 dpkg: error processing libsolid4 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libkio5:
  libkio5 depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
   Package libsolid4 is not configured yet.
 dpkg: error processing libkio5 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libknewstuff2-4:
  libknewstuff2-4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing libknewstuff2-4 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-pstricks:
  texlive-pstricks depends on texlive-generic-recommended (>= 2009-1); however:
   Package texlive-generic-recommended is not configured yet.
  texlive-pstricks depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-pstricks (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-math-extra:
  texlive-math-extra depends on texlive-fonts-recommended (>= 2009-1); however:
   Package texlive-fonts-recommended is not configured yet.
 dpkg: error processing texlive-math-extra (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libknotifyconfig4:
  libknotifyconfig4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing libknotifyconfig4 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of calligrasheets:
  calligrasheets depends on libkio5 (>= 4:4.4.0); however:
   Package libkio5 is not configured yet.
  calligrasheets depends on libknotifyconfig4 (>= 4:4.4.0); however:
   Package libknotifyconfig4 is not configured yet.
 dpkg: error processing calligrasheets (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of kdelibs-bin:
  kdelibs-bin depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing kdelibs-bin (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libknewstuff3-4:
  libknewstuff3-4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing libknewstuff3-4 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libkparts4:
  libkparts4 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing libkparts4 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-full:
  texlive-full depends on texlive-fonts-extra (>= 2009-1); however:
   Package texlive-fonts-extra is not configured yet.
  texlive-full depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
  texlive-full depends on texlive-math-extra (>= 2009-1); however:
   Package texlive-math-extra is not configured yet.
  texlive-full depends on texlive-formats-extra (>= 2009-1); however:
   Package texlive-formats-extra is not configured yet.
  texlive-full depends on texlive-pictures (>= 2009-1); however:
   Package texlive-pictures is not configured yet.
  texlive-full depends on texlive-pstricks (>= 2009-1); however:
   Package texlive-pstricks is not configured yet.
  texlive-full depends on texlive-fonts-recommended (>= 2009-1); however:
   Package texlive-fonts-recommended is not configured yet.
  texlive-full depends on texlive-generic-recommended (>= 2009-1); however:
   Package texlive-generic-recommended is not configured yet.
  texlive-full depends on texlive-luatex (>= 2009-1); however:
   Package texlive-luatex is not configured yet.
  texlive-full depends on context; however:
   Package context is not configured yet.
 dpkg: error processing texlive-full (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-latex-base:
  texlive-latex-base depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-latex-base (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of kdoctools:
  kdoctools depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
 dpkg: error processing kdoctools (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-lang-czechslovak:
  texlive-lang-czechslovak depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
  texlive-lang-czechslovak depends on texlive-latex-base (>= 2009-1); however:
   Package texlive-latex-base is not configured yet.
 dpkg: error processing texlive-lang-czechslovak (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of whoopsie:
  whoopsie depends on upstart-job; however:
   Package upstart-job is not installed.
   Package upstart which provides upstart-job is not configured yet.
 dpkg: error processing whoopsie (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of latex-sanskrit:
  latex-sanskrit depends on texlive-base; however:
   Package texlive-base is not configured yet.
 dpkg: error processing latex-sanskrit (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of texlive-generic-extra:
  texlive-generic-extra depends on texlive-base (>= 2009-1); however:
   Package texlive-base is not configured yet.
 dpkg: error processing texlive-generic-extra (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of latex-beamer:
  latex-beamer depends on texlive-latex-base; however:
   Package texlive-latex-base is not configured yet.
 dpkg: error processing latex-beamer (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of latex-cjk-common:
  latex-cjk-common depends on texlive-latex-base; however:
   Package texlive-latex-base is not configured yet.
 dpkg: error processing latex-cjk-common (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of libplasma3:
  libplasma3 depends on libkio5 (= 4:4.8.5-0ubuntu0.2); however:
   Package libkio5 is not configured yet.
  libplasma3 depends on libknewstuff3-4 (= 4:4.8.5-0ubuntu0.2); however:
   Package libknewstuff3-4 is not configured yet.
  libplasma3 depends on libsolid4 (= 4:4.8.5-0ubuntu0.2); however:
   Package libsolid4 is not configured yet.
 dpkg: error processing libplasma3 (--configure):
  dependency problems - leaving unconfigured
 dpkg: dependency problems prevent configuration of latex-cjk-thai:
  latex-cjk-thai depends on latex-cjk-common (>= 4.8.2+git20111216-1); however:
   Package latex-cjk-common is not configured yet.
  latex-cjk-thai depends on texlive-latex-base; however:
   Package texlive-latex-base is not configured yet.
 dpkg: error processing latex-cjk-thai (--configure):
  dependency problems - leaving unconfigured
 dpkg: too many errors, stopping
 Processing triggers for menu ...
 Processing triggers for tex-common ...
 texlive-base is not ready, delaying updmap-sys call
 Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
     This may take some time...  
 fmtutil-sys failed. Output has been stored in
 /tmp/fmtutil.W1dPSETT
 Please include this file if you report a bug.
 

 dpkg: error processing tex-common (--configure):
  subprocess installed post-installation script returned error exit status 1
 dpkg: too many errors, stopping
 Errors were encountered while processing:
  plymouth-x11
  mountall
  plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text
  plymouth-label
  upstart
  alsa-utils
  lightdm
  network-manager
  udev
  xdiagnose
  ubuntu-minimal
  rsyslog
  network-manager-gnome
  apport
  cups
  gdm
  texlive-base
  texlive-luatex
  texlive-generic-recommended
  texlive-fonts-recommended
  texlive-pictures
  apport-gtk
  texlive-fonts-extra
  context
  xserver-xorg-core
  xserver-xorg-video-openchrome
  dbus
  rhythmbox
  texlive-formats-extra
  libsolid4
  libkio5
  libknewstuff2-4
  texlive-pstricks
  texlive-math-extra
  libknotifyconfig4
  calligrasheets
  kdelibs-bin
  libknewstuff3-4
  libkparts4
  texlive-full
  texlive-latex-base
  kdoctools
  texlive-lang-czechslovak
  whoopsie
  latex-sanskrit
  texlive-generic-extra
  latex-beamer
  latex-cjk-common
  libplasma3
  latex-cjk-thai
  tex-common
```
 Processing was halted because there were too many errors.

---

