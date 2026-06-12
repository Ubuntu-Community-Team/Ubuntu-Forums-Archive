---
title: "[SOLVED] Failed to fetch"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Mouseball on 2008-02-11
sources.list
> 
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe 

message
> curt@curt-desktop:~$ sudo apt-get update
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release                                 
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release                         
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Sources                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Packages                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Packages                     
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages                   
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Sources                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages               
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages             
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Packages                           
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Packages                     
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Sources                            
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Sources                      
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Packages                       
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Packages                     
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages                   
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages             
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Sources                    
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Sources              
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages               
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages             
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Fetched 1B in 0s (1B/s)  
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/main/source/Sources.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/restricted/source/Sources.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/source/Sources.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/source/Sources.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71). - connect (101 Network is unreachable)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any guesses? this only started today, and it is preventing me from installing anything via apt-get or Add/Remove applications.

---

### Post by Partyboi2 on 2008-02-11
try changing the server from ca to another in Software Sources (System>Admin>Software Sources) first tab.

>  E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 			 		 	 	
Have you got another package manager open at the same time ie add/remove and synaptic  package manager? Or trying to update from terminal with another package manager opened at the same time?

---

### Post by Mouseball on 2008-02-11
yes and yes. i had A/R apps going on another workspace

you're good, looks like it's working.

---

