---
title: "Help !!! Dependency Problems ..."
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by james_bandido on 2008-06-20
my son turned off the computer while it was doing an update now i get this message :

[b]E: python-awn-trunk: subprocess post-installation script returned error exit status 1
E: awn-manager-trunk: dependency problems - leaving unconfigured[/b]

i already performed a dpkg --configure -a and this came up :
[b]james@bandido-laptop:~$ sudo dpkg --configure -a
Setting up python-awn-trunk (0.3.1~bzr306-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 awn-manager-trunk
james@bandido-laptop:~$ [/b]

what do i do now ?

---

### Post by Pumalite on 2008-06-20
Try sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by mpm on 2008-08-19
having a similar problem
dpkg --configure -a output:
Setting up python-awn-trunk (0.3.1~bzr467-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-trunk:
 avant-window-navigator-trunk depends on python-awn-trunk (>= 0.3.1~bzr467-hardy1-1); however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing avant-window-navigator-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-data-trunk:
 avant-window-navigator-data-trunk depends on avant-window-navigator-trunk (>= 0.3.1~bzr467-hardy1-1); however:
  Package avant-window-navigator-trunk is not configured yet.
dpkg: error processing avant-window-navigator-data-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 awn-manager-trunk
 avant-window-navigator-trunk
 avant-window-navigator-data-trunk

the recommended package upgrades resulted in no new packages, terminal output:
michael@michael-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vorbis-tools cd-discid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
michael@michael-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Fetched 1B in 22s (0B/s)
Reading package lists... Done
michael@michael-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I've been trying a few days to get awn to work correctly and was hoping that updates would resolve the situation.

Any help you could provide would be appreciated.

---

### Post by mpm on 2008-08-19
having a similar problem
dpkg --configure -a output:
Setting up python-awn-trunk (0.3.1~bzr467-hardy1-1) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-awn-trunk (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of awn-manager-trunk:
 awn-manager-trunk depends on python-awn-trunk; however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing awn-manager-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-trunk:
 avant-window-navigator-trunk depends on python-awn-trunk (>= 0.3.1~bzr467-hardy1-1); however:
  Package python-awn-trunk is not configured yet.
dpkg: error processing avant-window-navigator-trunk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of avant-window-navigator-data-trunk:
 avant-window-navigator-data-trunk depends on avant-window-navigator-trunk (>= 0.3.1~bzr467-hardy1-1); however:
  Package avant-window-navigator-trunk is not configured yet.
dpkg: error processing avant-window-navigator-data-trunk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-awn-trunk
 awn-manager-trunk
 avant-window-navigator-trunk
 avant-window-navigator-data-trunk

the recommended package upgrades resulted in no new packages, terminal output:
michael@michael-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vorbis-tools cd-discid
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
michael@michael-laptop:~$ sudo apt-get update
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Fetched 1B in 22s (0B/s)
Reading package lists... Done
michael@michael-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I've been trying a few days to get awn to work correctly and was hoping that updates would resolve the situation.

Any help you could provide would be appreciated.

---

### Post by Pumalite on 2008-08-19
Make sure all other apt-get processes are closed (Synaptic, etc)

---

