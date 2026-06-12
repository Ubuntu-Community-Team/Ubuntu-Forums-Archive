---
title: "Problem with upgrade"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by greyghost60 on 2008-03-10
Hi and Help
when I run the synapes installer or Add & remove the following appears

[http://www.getautomatix.com/apt/dists/gutsy/Release.gpg:](http://www.getautomatix.com/apt/dists/gutsy/Release.gpg:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
[http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2:](http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2:) Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
[http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release:) Unable to find expected entry  [http://archive.ubuntu.com/ubuntu/source/Sources](http://archive.ubuntu.com/ubuntu/source/Sources) in Meta-index file (malformed Release file?)

I have followed all the threads I can find, followed all the advice but to no avail. Is there anywhere I can get a clean sources.list so I can start again ? The NL one gives a 404 page not found. Or can someone tell what is going on?

Gerry (Greyghost60)

---

### Post by Pumalite on 2008-03-10
Post the output of:
sudo apt-get update
sudo apt-get upgrade

---

### Post by greyghost60 on 2008-03-10
from 
greyghost@greyghost-desktop:~$ sudo apt-get update
[sudo] password for greyghost:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/web Translation-en_GB            
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release.gpg [191B]                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Translation-en_GB                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/gutsy Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/deb-src Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Translation-en_GB            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/web Translation-en_GB                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/universe Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/multiverse Translation-en_GB            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/deb-src Translation-en_GB               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/gutsy Translation-en_GB                 
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release.gpg [191B]           
Get: 4 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/web Translation-en_GB           
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/gutsy Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/deb-src Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/main Translation-en_GB          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/universe Translation-en_GB      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB    
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security Release.gpg [191B]          
Get: 6 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/universe Translation-en_GB     
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg                              
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Get: 7 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB   
Get: 8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release.gpg [191B]         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/web Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/http://archive.ubuntu.com/ubuntu Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/deb-src Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/gutsy Translation-en_GB       
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Translation-en_GB        
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy Release                                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy/restricted Packages                     
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB                   
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/restricted Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/restricted Sources   
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/main Sources         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-security/multiverse Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB
Get: 9 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release [6702B]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Fetched 6710B in 0s (7800B/s)
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/Release.gpg](http://www.getautomatix.com/apt/dists/gutsy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  [http://archive.ubuntu.com/ubuntu/source/Sources](http://archive.ubuntu.com/ubuntu/source/Sources) in Meta-index file (malformed Release file?)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release)  Unable to find expected entry  screenlets/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://gb.archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

greyghost@greyghost-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greyghost@greyghost-desktop:~$ 
 hope this helps

greyghost

---

### Post by Pumalite on 2008-03-10
Try changing Server and post same output.

---

### Post by greyghost60 on 2008-03-10
Using main server previous was UK server
greyghost@greyghost-desktop:~$ sudo apt-get update
[sudo] password for greyghost:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/web Translation-en_GB            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/http://archive.ubuntu.com/ubuntu Translation-en_GB
Get: 2 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB                 
Get: 3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_GB       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/gutsy Translation-en_GB          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/deb-src Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_GB     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/web Translation-en_GB                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/deb-src Translation-en_GB                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/gutsy Translation-en_GB                    
Get: 4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]              
Get: 5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/web Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Get: 6 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release.gpg [189B]                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/gutsy Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/deb-src Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB       
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_GB        
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg                              
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB      
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [191B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/web Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/http://archive.ubuntu.com/ubuntu Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/deb-src Translation-en_GB        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/gutsy Translation-en_GB          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Ign [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy/screenlets Translation-en_GB              
Err [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB                   
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Get: 9 [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) gutsy Release [6702B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages
Fetched 6710B in 0s (9989B/s)                       
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/Release.gpg](http://www.getautomatix.com/apt/dists/gutsy/Release.gpg)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2](http://www.getautomatix.com/apt/dists/gutsy/main/i18n/Translation-en_GB.bz2)  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/Release)  Unable to find expected entry  screenlets/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release)  Unable to find expected entry  [http://archive.ubuntu.com/ubuntu/source/Sources](http://archive.ubuntu.com/ubuntu/source/Sources) in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release](http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/Release)  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
greyghost@greyghost-desktop:~$ 

From
greyghost@greyghost-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
greyghost@greyghost-desktop:~$ 

Hope this helps

---

### Post by Pumalite on 2008-03-10
Post:
cat /etc/apt/sources.list

---

### Post by corkythebung on 2008-03-10
Looks like [www.getautomatix.com](www.getautomatix.com) is down.

I googled it and if I click on the cached version I get a hit. The real (uncached) version returns an "Unable to connect" msg.

---

### Post by greyghost60 on 2008-03-10
Here is the output
greyghost@greyghost-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) universe gutsy deb-src main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted gutsy deb-src main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse web universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy



deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted deb-src gutsy universe main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

#AUTOMATIX REPOS END
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted universe gutsy deb-src main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy deb-src
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
greyghost@greyghost-desktop:~$ 

hope this helps
the problem was there before Automatrix went down though

---

### Post by corkythebung on 2008-03-11
Seems Automatix is back. I was having the "Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (64.69.36.51). - connect (111 Connection refused)" issue yesterday. I was upgrading from 7.04 to 7.10. Tried again today and there seems to be no issue now. Of course all this may be coincidence.

---

### Post by Pumalite on 2008-03-11
> **greyghost60 said:**
> Here is the output
greyghost@greyghost-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted web
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) universe gutsy deb-src main multiverse restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted gutsy deb-src main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse web universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy



deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted deb-src gutsy universe main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse #Added by software-properties

#AUTOMATIX REPOS END
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security web [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) restricted universe gutsy deb-src main multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy deb-src
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets
greyghost@greyghost-desktop:~$ 

hope this helps
the problem was there before Automatrix went down though

Hi:

Re: Automatix:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

