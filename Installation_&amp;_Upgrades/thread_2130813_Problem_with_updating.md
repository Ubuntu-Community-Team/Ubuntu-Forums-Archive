---
title: "Problem with updating"
date: 2013-03-30
forum: Installation &amp; Upgrades
---

### Post by jsavga on 2013-03-30
During recent update, It's finishing with error of could not update. I notice that each time I try to update when it begins, it says updates are already downloaded asnd then it tries to install them. I can't find where they're downloaded too, or how to dowqnload them again incase they were corrcupted in downloading.

Anyway, dropped to terminal and run

sudo apt-get update
sudo apt-get upgrade

and here is the output. I know there's an issue with the Gimp download, but it appears an issue with Gnome too. How can I redownload the updates?


[quote]
jsavga@jh-ubuntu-desktop:~$  sudo apt-get update
[sudo] password for jsavga: 
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release.gpg                           
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release.gpg                   
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal Release                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                              
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg [933 B]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal Release.gpg                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates Release                       
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release                                  
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Sources                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Sources                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources                             
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main i386 Packages                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted i386 Packages              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse i386 Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe i386 Packages                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                               
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources [14 B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Sources                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources [37.4 kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en             
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Sources                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources [15.9 kB]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en               
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner i386 Packages                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Sources            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free i386 Packages                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources [692 B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Sources              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main i386 Packages [100 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main i386 Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted i386 Packages      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse i386 Packages      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe i386 Packages        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_US                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en           
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted i386 Packages [14 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages [1,396 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages [45.0 kB]
Hit [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb Release                           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US             
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main i386 Packages                        
Hit [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games i386 Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/main Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/multiverse Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/restricted Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal/universe Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-updates/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/main Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) quantal-backports/universe Translation-en_US  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en_US               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/free Translation-en                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en_US           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) quantal/non-free Translation-en              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en                       
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en_US           
Ign [http://archive.getdeb.net](http://archive.getdeb.net) quantal-getdeb/games Translation-en
Fetched 251 kB in 14s (17.0 kB/s)
Reading package lists... Done
jsavga@jh-ubuntu-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gimp-data gnome-control-center gnome-control-center-data
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/16.4 MB of archives.
After this operation, 51.2 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 401785 files and directories currently installed.)
Preparing to replace gimp-data 2.8.4-1quantal0~ppa (using .../gimp-data_2.8.4-2quantal4~ppa_all.deb) ...
Unpacking replacement gimp-data ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gimp-data_2.8.4-2quantal4~ppa_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Preparing to replace gnome-control-center-data 1:3.4.2-0ubuntu19 (using .../gnome-control-center-data_1%3a3.4.2-0ubuntu19.1_all.deb) ...
Unpacking replacement gnome-control-center-data ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gnome-control-center-data_1%3a3.4.2-0ubuntu19.1_all.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Preparing to replace gnome-control-center 1:3.4.2-0ubuntu19 (using .../gnome-control-center_1%3a3.4.2-0ubuntu19.1_i386.deb) ...
Unpacking replacement gnome-control-center ...
dpkg-deb (subprocess): decompressing archive member: internal gzip read error: '<fd:4>: incorrect data check'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/gnome-control-center_1%3a3.4.2-0ubuntu19.1_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 /var/cache/apt/archives/gimp-data_2.8.4-2quantal4~ppa_all.deb
 /var/cache/apt/archives/gnome-control-center-data_1%3a3.4.2-0ubuntu19.1_all.deb
 /var/cache/apt/archives/gnome-control-center_1%3a3.4.2-0ubuntu19.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by dabl on 2013-03-30
Try these -- post back if one throws errors:

```
sudo apt-get clean
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by jsavga on 2013-03-30
Thanks, did the 

sudo apt-get clean
sudo apt-get update 

and then 

sudo apt-get upgrade

and all completed this time. apt-get clean is the command I was looking for. Didn't do the dist-upgrade.

---

### Post by dabl on 2013-03-30
Many people erroneously believe "dist-upgrade" will change the version of *buntu.  That is _not_ true.  "dist-upgrade" will _upgrade the current version_, including all packages and system files.

---

