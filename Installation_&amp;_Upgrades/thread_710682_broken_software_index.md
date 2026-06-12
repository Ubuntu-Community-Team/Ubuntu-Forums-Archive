---
title: "broken software index"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by xc00lxkidx on 2008-02-28
i tried to install some updates and i got a message saying i had a broken software index [dunno what that is, im new to linux]. it told me to run "sudo apt-get install -f"

i did that and got an error. heres what was on my terminal

ralfi@ralfi-laptop:~$ sudo apt-get install -f
[sudo] password for ralfi:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libawn-bzr
The following NEW packages will be installed:
  libawn-bzr
0 upgraded, 1 newly installed, 0 to remove and 49 not upgraded.
2 not fully installed or removed.
Need to get 0B/64.0kB of archives.
After unpacking 180kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libawn-bzr
Install these packages without verification [y/N]? y
(Reading database ... 117858 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr158-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn0
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr158-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ralfi@ralfi-laptop:~$

---

### Post by taurus on 2008-02-28
Maybe try these

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by xc00lxkidx on 2008-02-28
tried that and i still get the same error =/

heres my terminal

ralfi@ralfi-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of awn-core-applets-bzr:
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
dpkg: error processing awn-core-applets-bzr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not installed.
dpkg: error processing python-libawn-bzr (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 awn-core-applets-bzr
 python-libawn-bzr
ralfi@ralfi-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                      
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Get:5 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Get:8 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release [10.9kB]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [191B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                 
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release                                
Ign [http://javadesktop.org](http://javadesktop.org) stable Release.gpg                                 
Ign [http://javadesktop.org](http://javadesktop.org) stable/contrib Translation-en_US
Ign [http://javadesktop.org](http://javadesktop.org) stable Release              
Ign [http://javadesktop.org](http://javadesktop.org) stable/contrib Packages     
Get:11 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages [3174B]
Hit [http://javadesktop.org](http://javadesktop.org) stable/contrib Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release
Get:12 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources [1351B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [245kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources [68.1kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources [937B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [68.2kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources [10.6kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [9942B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources [1883B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Fetched 483kB in 3s (157kB/s)
Reading package lists... Done
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3E231AC7F4ECF181
W: You may want to run apt-get update to correct these problems

---

### Post by xc00lxkidx on 2008-02-28
help anyone? please?

---

### Post by zvacet on 2008-02-29
Make sure that you have all repos open in system>admin<software sources check all boxes unser Ubuntu software and updates tab.Reload.Type in terminal

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3E231AC7F4ECF181
gpg --export --armor 3E231AC7F4ECF181 | sudo apt-key add -

after that 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by xc00lxkidx on 2008-03-02
when i typed "sudo apt-get update && sudo apt-get upgrade" into the terminal i got this:

ralfi@ralfi-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:3 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release.gpg [189B]                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Get:7 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy Release [10.9kB]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US  
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release
Get:9 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Packages [3174B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Get:10 [http://download.tuxfamily.org](http://download.tuxfamily.org) gutsy/avant-window-navigator Sources [1351B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Fetched 15.6kB in 2s (7424B/s)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ralfi@ralfi-laptop:~$

---

### Post by taurus on 2008-03-02
If you have Add/Remove or synaptic running, close it first before you run that command from a terminal.

---

### Post by xc00lxkidx on 2008-03-02
tried that. when i tried to reopen synaptic i got this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by xc00lxkidx on 2008-03-03
please help my synaptic is completely dead

---

### Post by xc00lxkidx on 2008-03-03
ok so i ran "sudo dpkg --configure -a"  like synaptic said. i got this output:

ralfi@ralfi-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of awn-core-applets-bzr:
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
 awn-core-applets-bzr depends on libawn-bzr; however:
  Package libawn-bzr is not installed.
dpkg: error processing awn-core-applets-bzr (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-libawn-bzr:
 python-libawn-bzr depends on libawn-bzr (= 0.2.0-bzr158-1); however:
  Package libawn-bzr is not installed.
dpkg: error processing python-libawn-bzr (--configure):
 dependency problems - leaving unconfigured
Setting up lg3d-core (1.0.0+rc1) ...
/usr/share/lg3d/bin/postinstall: line 10: /bin/arch: Permission denied
/usr/share/lg3d/bin/../bin/add-lg-to-gdm: line 28: /bin/arch: Permission denied
Success. LG has been added as a gdm session.
/usr/share/lg3d/bin/postinstall: line 43: cd: /usr/share/lg3d/bin/../lib/linux-/lg3d-x11/programs/Xserver: No such file or directory
chown: cannot access `Xorg': No such file or directory
chgrp: cannot access `Xorg': No such file or directory
chmod: cannot access `Xorg': No such file or directory
dpkg: error processing lg3d-core (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 awn-core-applets-bzr
 python-libawn-bzr
 lg3d-core
ralfi@ralfi-laptop:~$

---

