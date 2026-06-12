---
title: "Broken packages. Cannot install/remove anything"
date: 2016-03-27
forum: Installation &amp; Upgrades
---

### Post by archimedes1981 on 2016-03-27
Hi, some months ago I upgraded from 12.04 to 14.04 and I had kodi 14 installed. I just upgraded kodi to 16 and now I can't install/remove/update anything. I looked it upa nd I can't understand how to fix it. Anyone can help? I'm familiar with linux since I've used it for quite some years now but I'm no expert.

carabott@MediaCentre:~$ sudo apt-get install kodi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kodi is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kodi-bin : Depends: libsdl2-2.0-0 (>= 2.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
carabott@MediaCentre:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsdl2-2.0-0
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0 B/317 kB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 475813 files and directories currently installed.)
Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb ...
Unpacking libsdl2-2.0-0:amd64 (2.0.2+dfsg1-3ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2:amd64 2.0.3+z4~20140315-8621-1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
carabott@MediaCentre:~$

---

### Post by oldfred on 2016-03-27
One of your errors mentions ppa1precise1.

So do you have a ppa still using precise?
Often issues related to ppa's that are not updated cause these types of errors.

---

### Post by archimedes1981 on 2016-03-27
Can you suggest anything? should I clear all repositories? I wouldn't know ehere to get fresh ones.

---

### Post by AnrDaemon on 2016-03-27
Check the ```
/etc/apt/sources.list.d/*.list
``` for any stray references, and remove those you find obsolete.

---

### Post by archimedes1981 on 2016-03-27
still same I think

```
carabott@MediaCentre:~$ cd /etc/apt/sources.list.d/
carabott@MediaCentre:/etc/apt/sources.list.d$ ls
google-chrome.list                       precise-partner.list.save
google-chrome.list.save                  team-xbmc-ppa-precise.list
opensync-opensync-0_22-trusty.list       team-xbmc-ppa-precise.list.distUpgrade
opensync-opensync-0_22-trusty.list.save  team-xbmc-ppa-precise.list.save
precise-partner.list                     team-xbmc-ppa-trusty.list
precise-partner.list.distUpgrade         team-xbmc-ppa-trusty.list.save
carabott@MediaCentre:/etc/apt/sources.list.d$ sudo rm precise-partner.list
[sudo] password for carabott: 
carabott@MediaCentre:/etc/apt/sources.list.d$ sudo rm precise-partner.list.*
carabott@MediaCentre:/etc/apt/sources.list.d$ ls
google-chrome.list                       team-xbmc-ppa-precise.list.distUpgrade
google-chrome.list.save                  team-xbmc-ppa-precise.list.save
opensync-opensync-0_22-trusty.list       team-xbmc-ppa-trusty.list
opensync-opensync-0_22-trusty.list.save  team-xbmc-ppa-trusty.list.save
team-xbmc-ppa-precise.list
carabott@MediaCentre:/etc/apt/sources.list.d$ sudo rm team-xbmc-ppa-precise.list*
carabott@MediaCentre:/etc/apt/sources.list.d$ ls
google-chrome.list                  opensync-opensync-0_22-trusty.list.save
google-chrome.list.save             team-xbmc-ppa-trusty.list
opensync-opensync-0_22-trusty.list  team-xbmc-ppa-trusty.list.save
carabott@MediaCentre:/etc/apt/sources.list.d$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsdl2-2.0-0
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
2 not fully installed or removed.
Need to get 0 B/317 kB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 475813 files and directories currently installed.)
Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb ...
Unpacking libsdl2-2.0-0:amd64 (2.0.2+dfsg1-3ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2:amd64 2.0.3+z4~20140315-8621-1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
carabott@MediaCentre:/etc/apt/sources.list.d$
```

---

### Post by AnrDaemon on 2016-03-27
1. Do "apt-get update" after changing the list of repositories.
2. Use aptitude and force uninstall of your current libsdl2 when installing the one from main repo.

P.S.
You can safely remove *.save clutter, btw.

---

### Post by oldfred on 2016-03-27
If you have upgraded to trusty, you should not have any references to precise.

Part of upgrade is to remove all ppa's as they do not auto convert. And then you may be able to re-enable new ppa if required.

---

### Post by archimedes1981 on 2016-04-02
Looks ok now. Thanks everyone for the help:

```
carabott@MediaCentre:~$ sudo apt-get update
[sudo] password for carabott: 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty InRelease                                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [181 B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Get:2 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security InRelease [65.9 kB]              
Get:3 [http://dl.google.com](http://dl.google.com) stable Release [1,189 B]                            
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Get:5 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,384 B]                
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:6 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Sources [110 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Get:7 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Sources [4,035 B]     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Get:8 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Sources [2,750 B]     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:9 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Sources [34.7 kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Get:10 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main amd64 Packages [448 kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:11 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted amd64 Packages [13.0 kB]
Get:12 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse amd64 Packages [4,991 B]
Get:13 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe amd64 Packages [126 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                 
Get:14 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main i386 Packages [422 kB]
Get:15 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted i386 Packages [12.7 kB]
Get:16 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse i386 Packages [5,175 B]
Get:17 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe i386 Packages [126 kB]
Get:18 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Translation-en [244 kB]
Get:19 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Translation-en [2,570 B]
Get:20 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Translation-en [3,206 B]
Get:21 [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Translation-en [74.3 kB]
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release              
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en_US
Fetched 1,702 kB in 5s (305 kB/s)                  
Reading package lists... Done
carabott@MediaCentre:~$ sudo dpkg -r libsdl2
(Reading database ... 475812 files and directories currently installed.)
Removing libsdl2:amd64 (2.0.3+z4~20140315-8621-1ppa1precise1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
carabott@MediaCentre:~$ sudo apt-get install libsdl2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl2:i386

E: Package 'libsdl2' has no installation candidate
carabott@MediaCentre:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty InRelease                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security InRelease                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Sources                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted amd64 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse amd64 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe i386 Packages             
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Translation-en                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Translation-en          
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Translation-en          
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Translation-en            
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US             
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Sources 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                          
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Sources              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Sources
Hit [http://dl.google.com](http://dl.google.com) stable Release                          
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main amd64 Packages            
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages               
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted amd64 Packages      
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse amd64 Packages      
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe amd64 Packages        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main i386 Packages             
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted i386 Packages       
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse i386 Packages         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe i386 Packages           
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en              
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US             
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en       
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en_US
Reading package lists... Done
carabott@MediaCentre:~$ sudo apt0get -f install libsdl2
sudo: apt0get: command not found
carabott@MediaCentre:~$ sudo apt-get install -f libsdl2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl2:i386

E: Package 'libsdl2' has no installation candidate
carabott@MediaCentre:~$ sudo dpkg -r libsdl2:i386
dpkg: warning: ignoring request to remove libsdl2:i386, only the config
 files of which are on the system; use --purge to remove them too
carabott@MediaCentre:~$ sudo dpkg -r libsdl2:i386 --purge
dpkg: error: --remove needs a valid package name but '--purge' is not: illegal package name in specifier '--purge': must start with an alphanumeric character

Type dpkg --help for help about installing and deinstalling packages
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked
[*] produce a lot of output - pipe it through 'less' or 'more' !
carabott@MediaCentre:~$ apt 
apt 1.0.1ubuntu2 for amd64 compiled on Oct  8 2014 12:36:19
Usage: apt [options] command

CLI for apt.
Basic commands: 
 list - list packages based on package names
 search - search in package descriptions
 show - show package details

 update - update list of available packages

 install - install packages
 remove  - remove packages

 upgrade - upgrade the system by installing/upgrading packages
 full-upgrade - upgrade the system by removing/installing/upgrading packages

 edit-sources - edit the source information file
carabott@MediaCentre:~$ apt remove libsdl2:i386
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
carabott@MediaCentre:~$ sudo apt remove libsdl2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libsdl2:i386' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kodi-bin : Depends: libsdl2-2.0-0 (>= 2.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
carabott@MediaCentre:~$ sudo apt-get --force install libsdl2
E: Command line option --force is not understood
carabott@MediaCentre:~$ sudo apt-get -f install libsdl2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libsdl2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsdl2:i386

E: Package 'libsdl2' has no installation candidate
carabott@MediaCentre:~$ sudo dpkg --purge --force-all libsdl2
(Reading database ... 475803 files and directories currently installed.)
Removing libsdl2:amd64 (2.0.3+z4~20140315-8621-1ppa1precise1) ...
Purging configuration files for libsdl2:amd64 (2.0.3+z4~20140315-8621-1ppa1precise1) ...
carabott@MediaCentre:~$ sudo apt-get update
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty InRelease                                   
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security InRelease                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources                               
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release.gpg                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Sources                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Sources                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted amd64 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse amd64 Packages          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe amd64 Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main i386 Packages                 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse i386 Packages           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe i386 Packages             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/main Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/multiverse Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/restricted Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty-security/universe Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty Release        
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Sources
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe amd64 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe i386 Packages
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en
Hit [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/main Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/multiverse Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/restricted Translation-en_US
Ign [http://ftp.uni-mainz.de](http://ftp.uni-mainz.de) trusty/universe Translation-en_US
Reading package lists... Done
carabott@MediaCentre:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libsdl2-2.0-0
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
2 not fully installed or removed.
Need to get 0 B/317 kB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 475804 files and directories currently installed.)
Preparing to unpack .../libsdl2-2.0-0_2.0.2+dfsg1-3ubuntu1_amd64.deb ...
Unpacking libsdl2-2.0-0:amd64 (2.0.2+dfsg1-3ubuntu1) ...
Setting up libsdl2-2.0-0:amd64 (2.0.2+dfsg1-3ubuntu1) ...
Setting up kodi-bin (2:16.0~git20160220.1654-final-0trusty) ...
Setting up kodi (2:16.0~git20160220.1654-final-0trusty) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for menu (2.1.46ubuntu1) ...
carabott@MediaCentre:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable libbluray1 libcec2 libmatroska6 libnfs1 libpcre3
  libpcre3:i386 libpcrecpp0 libshairplay0 libtag1-vanilla libtag1-vanilla:i386
  libtag1c2a libtag1c2a:i386 tzdata xbmc xbmc-pvr-argustv xbmc-pvr-dvbviewer
  xbmc-pvr-mediaportal-tvserver xbmc-pvr-mythtv-cmyth xbmc-pvr-nextpvr
  xbmc-pvr-njoy xbmc-pvr-tvheadend-hts xbmc-pvr-vdr-vnsi xbmc-pvr-vuplus
24 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.8 MB of archives.
After this operation, 217 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ftp.uni-mainz.de/ubuntu/](http://ftp.uni-mainz.de/ubuntu/) trusty-security/main libpcre3 i386 1:8.31-2ubuntu2.2 [141 kB]
Get:2 [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main google-chrome-stable amd64 49.0.2623.110-1 [48.7 MB]
Get:3 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libbluray1 amd64 1:0.8.1-1~trusty [110 kB]
Get:4 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libnfs1 amd64 1.6.0-0~ppa1~trusty [41.4 kB]
Get:5 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libtag1-vanilla i386 1.9.1-2.2~ppa~trusty [283 kB]
Get:6 [http://ftp.uni-mainz.de/ubuntu/](http://ftp.uni-mainz.de/ubuntu/) trusty-security/main libpcre3 amd64 1:8.31-2ubuntu2.2 [144 kB]
Get:7 [http://ftp.uni-mainz.de/ubuntu/](http://ftp.uni-mainz.de/ubuntu/) trusty-security/universe libmatroska6 amd64 1.4.1-2+deb8u1build0.14.04.1 [107 kB]
Get:8 [http://ftp.uni-mainz.de/ubuntu/](http://ftp.uni-mainz.de/ubuntu/) trusty-security/main libpcrecpp0 amd64 1:8.31-2ubuntu2.2 [14.5 kB]
Get:9 [http://ftp.uni-mainz.de/ubuntu/](http://ftp.uni-mainz.de/ubuntu/) trusty-security/main tzdata all 2016c-0ubuntu0.14.04 [166 kB]
Get:10 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libtag1-vanilla amd64 1.9.1-2.2~ppa~trusty [284 kB]
Get:11 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libtag1c2a amd64 1.9.1-2.2~ppa~trusty [17.7 kB]
Get:12 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libtag1c2a i386 1.9.1-2.2~ppa~trusty [17.7 kB]
Get:13 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libshairplay0 amd64 0.9.2-2~trusty [45.3 kB]
Get:14 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main libcec2 amd64 2.2.0-2~trusty [169 kB]
Get:15 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc all 2:16.0~git20160220.1654-final-0trusty [37.5 kB]
Get:16 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-argustv amd64 1.9.176-14trusty [188 kB]
Get:17 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-dvbviewer amd64 1.9.13-14trusty [114 kB]
Get:18 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-mediaportal-tvserver amd64 1.9.13-14trusty [217 kB]
Get:19 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-mythtv-cmyth amd64 1.9.16-14trusty [345 kB]
Get:20 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-nextpvr amd64 1.9.7-14trusty [137 kB]
Get:21 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-njoy amd64 1.9.5-14trusty [79.9 kB]
Get:22 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-tvheadend-hts amd64 1.9.27-14trusty [170 kB]
Get:23 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-vdr-vnsi amd64 1.9.8-14trusty [145 kB]
Get:24 [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/) trusty/main xbmc-pvr-vuplus amd64 1.9.11-14trusty [128 kB]
Fetched 51.8 MB in 32s (1,585 kB/s)                                            
Preconfiguring packages ...
(Reading database ... 475813 files and directories currently installed.)
Preparing to unpack .../libpcre3_1%3a8.31-2ubuntu2.2_amd64.deb ...
De-configuring libpcre3:i386 (1:8.31-2ubuntu2.1) ...
Unpacking libpcre3:amd64 (1:8.31-2ubuntu2.2) over (1:8.31-2ubuntu2.1) ...
Preparing to unpack .../libpcre3_1%3a8.31-2ubuntu2.2_i386.deb ...
Unpacking libpcre3:i386 (1:8.31-2ubuntu2.2) over (1:8.31-2ubuntu2.1) ...
Preparing to unpack .../google-chrome-stable_49.0.2623.110-1_amd64.deb ...
Unpacking google-chrome-stable (49.0.2623.110-1) over (49.0.2623.108-1) ...
Preparing to unpack .../libbluray1_1%3a0.8.1-1~trusty_amd64.deb ...
Unpacking libbluray1:amd64 (1:0.8.1-1~trusty) over (1:0.5.0-1) ...
Preparing to unpack .../libmatroska6_1.4.1-2+deb8u1build0.14.04.1_amd64.deb ...
Unpacking libmatroska6:amd64 (1.4.1-2+deb8u1build0.14.04.1) over (1.4.1-2) ...
Preparing to unpack .../libnfs1_1.6.0-0~ppa1~trusty_amd64.deb ...
Unpacking libnfs1:amd64 (1.6.0-0~ppa1~trusty) over (1.6.0-0~ppa1~precise) ...
Preparing to unpack .../libpcrecpp0_1%3a8.31-2ubuntu2.2_amd64.deb ...
Unpacking libpcrecpp0:amd64 (1:8.31-2ubuntu2.2) over (1:8.31-2ubuntu2.1) ...
Preparing to unpack .../libtag1-vanilla_1.9.1-2.2~ppa~trusty_amd64.deb ...
De-configuring libtag1-vanilla:i386 (1.9.1-2) ...
Unpacking libtag1-vanilla:amd64 (1.9.1-2.2~ppa~trusty) over (1.9.1-2) ...
Preparing to unpack .../libtag1-vanilla_1.9.1-2.2~ppa~trusty_i386.deb ...
Unpacking libtag1-vanilla:i386 (1.9.1-2.2~ppa~trusty) over (1.9.1-2) ...
Preparing to unpack .../libtag1c2a_1.9.1-2.2~ppa~trusty_amd64.deb ...
De-configuring libtag1c2a:i386 (1.9.1-2) ...
Unpacking libtag1c2a:amd64 (1.9.1-2.2~ppa~trusty) over (1.9.1-2) ...
Preparing to unpack .../libtag1c2a_1.9.1-2.2~ppa~trusty_i386.deb ...
Unpacking libtag1c2a:i386 (1.9.1-2.2~ppa~trusty) over (1.9.1-2) ...
Preparing to unpack .../libshairplay0_0.9.2-2~trusty_amd64.deb ...
Unpacking libshairplay0:amd64 (0.9.2-2~trusty) over (0.9.0-6~precise) ...
Preparing to unpack .../tzdata_2016c-0ubuntu0.14.04_all.deb ...
Unpacking tzdata (2016c-0ubuntu0.14.04) over (2016b-0ubuntu0.14.04) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for menu (2.1.46ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up tzdata (2016c-0ubuntu0.14.04) ...

Current default time zone: 'Europe/Malta'
Local time is now:      Sat Apr  2 11:01:06 CEST 2016.
Universal Time is now:  Sat Apr  2 09:01:06 UTC 2016.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 475813 files and directories currently installed.)
Preparing to unpack .../libcec2_2.2.0-2~trusty_amd64.deb ...
Unpacking libcec2:amd64 (2.2.0-2~trusty) over (2.2.0-2~precise) ...
Preparing to unpack .../xbmc_2%3a16.0~git20160220.1654-final-0trusty_all.deb ...
Unpacking xbmc (2:16.0~git20160220.1654-final-0trusty) over (2:14.2~git20150327.1058-final-0precise) ...
Preparing to unpack .../xbmc-pvr-argustv_1.9.176-14trusty_amd64.deb ...
Unpacking xbmc-pvr-argustv (1.9.176-14trusty) over (1.9.176-14precise) ...
Preparing to unpack .../xbmc-pvr-dvbviewer_1.9.13-14trusty_amd64.deb ...
Unpacking xbmc-pvr-dvbviewer (1.9.13-14trusty) over (1.9.13-14precise) ...
Preparing to unpack .../xbmc-pvr-mediaportal-tvserver_1.9.13-14trusty_amd64.deb ...
Unpacking xbmc-pvr-mediaportal-tvserver (1.9.13-14trusty) over (1.9.13-14precise) ...
Preparing to unpack .../xbmc-pvr-mythtv-cmyth_1.9.16-14trusty_amd64.deb ...
Unpacking xbmc-pvr-mythtv-cmyth (1.9.16-14trusty) over (1.9.16-14precise) ...
Preparing to unpack .../xbmc-pvr-nextpvr_1.9.7-14trusty_amd64.deb ...
Unpacking xbmc-pvr-nextpvr (1.9.7-14trusty) over (1.9.7-14precise) ...
Preparing to unpack .../xbmc-pvr-njoy_1.9.5-14trusty_amd64.deb ...
Unpacking xbmc-pvr-njoy (1.9.5-14trusty) over (1.9.5-14precise) ...
Preparing to unpack .../xbmc-pvr-tvheadend-hts_1.9.27-14trusty_amd64.deb ...
Unpacking xbmc-pvr-tvheadend-hts (1.9.27-14trusty) over (1.9.27-14precise) ...
Preparing to unpack .../xbmc-pvr-vdr-vnsi_1.9.8-14trusty_amd64.deb ...
Unpacking xbmc-pvr-vdr-vnsi (1.9.8-14trusty) over (1.9.8-14precise) ...
Preparing to unpack .../xbmc-pvr-vuplus_1.9.11-14trusty_amd64.deb ...
Unpacking xbmc-pvr-vuplus (1.9.11-14trusty) over (1.9.11-14precise) ...
Setting up libpcre3:i386 (1:8.31-2ubuntu2.2) ...
Setting up libpcre3:amd64 (1:8.31-2ubuntu2.2) ...
Setting up google-chrome-stable (49.0.2623.110-1) ...
Setting up libbluray1:amd64 (1:0.8.1-1~trusty) ...
Setting up libmatroska6:amd64 (1.4.1-2+deb8u1build0.14.04.1) ...
Setting up libnfs1:amd64 (1.6.0-0~ppa1~trusty) ...
Setting up libpcrecpp0:amd64 (1:8.31-2ubuntu2.2) ...
Setting up libtag1-vanilla:i386 (1.9.1-2.2~ppa~trusty) ...
Setting up libtag1-vanilla:amd64 (1.9.1-2.2~ppa~trusty) ...
Setting up libtag1c2a:i386 (1.9.1-2.2~ppa~trusty) ...
Setting up libtag1c2a:amd64 (1.9.1-2.2~ppa~trusty) ...
Setting up libshairplay0:amd64 (0.9.2-2~trusty) ...
Setting up libcec2:amd64 (2.2.0-2~trusty) ...
Setting up xbmc (2:16.0~git20160220.1654-final-0trusty) ...
Setting up xbmc-pvr-argustv (1.9.176-14trusty) ...
Setting up xbmc-pvr-dvbviewer (1.9.13-14trusty) ...
Setting up xbmc-pvr-mediaportal-tvserver (1.9.13-14trusty) ...
Setting up xbmc-pvr-mythtv-cmyth (1.9.16-14trusty) ...
Setting up xbmc-pvr-nextpvr (1.9.7-14trusty) ...
Setting up xbmc-pvr-njoy (1.9.5-14trusty) ...
Setting up xbmc-pvr-tvheadend-hts (1.9.27-14trusty) ...
Setting up xbmc-pvr-vdr-vnsi (1.9.8-14trusty) ...
Setting up xbmc-pvr-vuplus (1.9.11-14trusty) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
Processing triggers for menu (2.1.46ubuntu1) ...
carabott@MediaCentre:~$
```

---

### Post by AnrDaemon on 2016-04-02
=d>

---

### Post by yoshii on 2016-04-02
please mark the thread as [SOLVED] so it can help future users faster.

---

