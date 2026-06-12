---
title: "Can't update firefox"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by spoonman7724 on 2011-11-23
When I updated Ubuntu to 11.10, firefox somehow reverted to 3.5.1 (i forget what I was at before, maybe 7?), and I can't update it.  I've tried updating it "normally" as well as uninstalling it and reinstalling it, but even when I download Firefox 8 from the Mozilla website, it installs 3.5.1.  When I try updating in the terminal I get this message:


After this operation, 38.5 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 520361 files and directories currently installed.)
Removing firefox-globalmenu ...
Removing firefox ...
Purging configuration files for firefox ...
dpkg: warning: while removing firefox, directory '/usr/lib/firefox-addons/plugins' not empty so not removed.
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Processing triggers for menu ...
jordan@jordan-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,349 B]                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release      
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,220 B]                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [630 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Fetched 4,942 B in 2s (1,998 B/s)
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


Thanks for any help.

---

### Post by ajgreeny on 2011-11-23
I am not sure if this is your situation, but I believe it is much better to purge all your ppa and other non-standard repos when doing a distro upgrade online, if that is what you did.  You seem to have a lot of ppa and other repos enabled, so it is probably a good idea to go to software-sources and disable them all for now, then try updating the system again with ```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by spoonman7724 on 2011-11-23
still not working with all that... any other ideas?

---

### Post by ajgreeny on 2011-11-24
Install synaptic and try using that to see what versions of firefox are available.

Synaptic is much better than the software-center in my opinion;  I have never actually used the software-center on my system.

---

### Post by spoonman7724 on 2011-11-24
> **ajgreeny said:**
> Install synaptic and try using that to see what versions of firefox are available.

Synaptic is much better than the software-center in my opinion;  I have never actually used the software-center on my system.

When I do it through Synaptic I get the error:


"E: firefox: subprocess installed post-installation script returned error exit status 2
E: firefox-globalmenu: dependency problems - leaving unconfigured"

The full message from the terminal is: 

"Selecting previously deselected package firefox.
(Reading database ... 198816 files and directories currently installed.)
Unpacking firefox (from .../firefox_8.0+build1-0ubuntu0.11.10.3_i386.deb) ...
Selecting previously deselected package firefox-globalmenu.
Unpacking firefox-globalmenu (from .../firefox-globalmenu_8.0+build1-0ubuntu0.11.10.3_i386.deb) ...
Selecting previously deselected package xul-ext-ubufox.
Unpacking xul-ext-ubufox (from .../xul-ext-ubufox_1.0-0ubuntu2.1_all.deb) ...
Selecting previously deselected package ubufox.
Unpacking ubufox (from .../ubufox_1.0-0ubuntu2.1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up firefox (8.0+build1-0ubuntu0.11.10.3) ...
***Your system has been left in a broken state by a third party package***
This is usually caused by installing packages from Ubuntuzilla. Fixing this now
dpkg-divert: error: mismatch on package
  when removing `diversion of /usr/bin/firefox by firefox'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 8.0+build1-0ubuntu0.11.10.3); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
Setting up xul-ext-ubufox (1.0-0ubuntu2.1) ...
No apport report written because MaxReports is reached already
                                                              localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox (8.0+build1-0ubuntu0.11.10.3) ...
***Your system has been left in a broken state by a third party package***
This is usually caused by installing packages from Ubuntuzilla. Fixing this now
dpkg-divert: error: mismatch on package
  when removing `diversion of /usr/bin/firefox by firefox'
  found `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg: error processing firefox (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 8.0+build1-0ubuntu0.11.10.3); however:
  Package firefox is not configured yet.
dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 firefox
 firefox-globalmenu"

---

### Post by ajgreeny on 2011-11-25
It looks as if you need to purge FF to get rid of the problem package and then try re-installing it through synaptic again.

Perhaps the FF from ubuntuzilla, or wherever you got it, is not compatible with the various packages in 11.10 that seem to be causing breakage.

---

