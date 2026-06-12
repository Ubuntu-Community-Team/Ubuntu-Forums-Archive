---
title: "I can't install any applications!"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by TonyKmau on 2007-12-01
I've been running ubuntu for a couple days now, but i'm seriously considering switching back to XP.

I am finding that 9/10 my installations will fail. 

When I install through Synaptic Package Manager I nearly always get this message. Same with the Add/Remove Applications 
> Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

When I run a .deb package installer 
> Could not download all required files
details: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/u/unixodbc/unixodbc_2.2.11-16_i386.deb Hash Sum mismatch

When I 'sudo apt-get update' in the terminal i get:
> tony@tony-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Translation-en_GB
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release.gpg                         
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Translation-en_GB              
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Translation-en_GB          
Get: 1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                  
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_GB               
Get: 3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_GB               
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release.gpg                                  
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Translation-en_GB                       
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Translation-en_GB                   
Get: 4 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [378B]                           
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_GB                          
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy Release                             
Get: 5 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release.gpg [307B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_GB                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_GB               
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_GB       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy Release                                      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_GB                 
Hit [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Translation-en_GB             
Err [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Translation-en_GB      
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Translation-en_GB        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Translation-en_GB      
Ign [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
Get: 8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_GB            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_GB      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_GB        
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
Get: 9 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release [17.0kB]               
Get: 10 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]                            
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main Packages                       
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_GB             
Ign [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Err [http://ntfs-3g.sitesweetsite.info](http://ntfs-3g.sitesweetsite.info) edgy/main-all Packages                   
  404 Not Found
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                           
Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main Packages                                
  404 Not Found
Ign [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                           
[B]Err [http://flomertens.keo.in](http://flomertens.keo.in) edgy/main-all Packages                            
  404 Not Found[/B]
Get: 11 [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas/all Packages [9597B]          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/main Sources                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/universe Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security/multiverse Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages           
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages                         
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                       
Fetched 85.5kB in 8s (10.4kB/s)                                                
[B]Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/main Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071017)_dists_gutsy_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017) gutsy/restricted Packages (/var/lib/apt/lists/Ubuntu%207.10%20%5fGutsy%20Gibbon%5f%20-%20Release%20i386%20(20071017)_dists_gutsy_restricted_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead[/B].


and when i attempt to install via the terminal
> tony@tony-desktop:~$ sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libarts1c2a libartsc0 debhelper intltool-debian libbeecrypt6
  fftw3 kdelibs-data libxcb-xv0 po-debconf ruby1.8 libxcb1 gettext python-qt3
  ruby libavahi-qt3-1 python-sip4 libxcb-shape0 tcltls libifp4
  libdbus-qt-1-1c2 dpkg-dev libxvmc1 libpq5 html2text libpulse0 libqt3-mt
  patch libruby1.8 libaudio2 libxcb-shm0 libid3-3.8.3c2a libnjb5 libofa0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libid3tag0 libmad0 libmodplug0c2 libmpcdec3 ttf-dejavu ttf-dejavu-extra
  vlc-nox
Recommended packages:
  videolan-doc
The following NEW packages will be installed
  libid3tag0 libmad0 libmodplug0c2 libmpcdec3 mozilla-plugin-vlc ttf-dejavu
  ttf-dejavu-extra vlc vlc-nox vlc-plugin-esd
0 upgraded, 10 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/8814kB of archives.
After unpacking 22.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
[B]Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.19-1ubuntu3_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
[/B]

---

### Post by TonyKmau on 2007-12-01
I also seem to be having a problems with downloading from some repositories

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found
[http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz:](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz:) 404 Not Found
[http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:) 404 Not Found
[http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz:) 404 Not Found


> An error occured:

W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277

---

### Post by kay65535 on 2007-12-07
> **TonyKmau said:**
> /pool/main/libi/libid3tag/libid3tag0_0.15.1b-10_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmad/libmad0_0.15.1b-2.1ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmodplug/libmodplug0c2_0.7-5.2ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/t/ttf-dejavu/ttf-dejavu-extra_2.19-1ubuntu3_all.deb Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Hmm. It looks like you are trying to get the programs off of the CD, and you need to get them from the internet. You have to deactivate it in the Synaptic configuration. Try opening Synaptic (the "System -> Administration -> Synaptic" menu), Then Click on Configuration -> Repositories, and try to configure it to not use the CDs, and to use internet.

Hope this helps.

---

### Post by PmDematagoda on 2007-12-07
Concerning the 404 errors you get, go to System>Administration>Software Sources and change the location of the server.

After you do that, reload the sources list when it tells you to, if it succeeds then the problem is solved.

---

