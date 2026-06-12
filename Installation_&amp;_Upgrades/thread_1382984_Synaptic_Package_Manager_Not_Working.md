---
title: "Synaptic Package Manager Not Working"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by Daedalus.Maelstrom on 2010-01-16
Hi,

I'm new to Linux,

After installing the 'getdeb' and 'playdeb' debian packages that
automate adding those repositories for
[http://www.getdeb.net/updates/ubuntu/9.10/](http://www.getdeb.net/updates/ubuntu/9.10/)
and
[http://www.playdeb.net/updates/ubuntu/9.10/](http://www.playdeb.net/updates/ubuntu/9.10/)
my synaptic package manager started acting up
giving me this error:

ould not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Problem executing scripts APT::Update::Pre-Invoke '/usr/bin/daptup --pre'Sub-process returned an error code

Does anyone know how to fix this? I am a long haul 48 state truck driver and it may be a couple days between replies until I can get to the next Wi-Fi hotspot.

(running Linux Ubuntu v9.10 (Karmic Koala) on a Toshiba Satellite A105-S4274)

---

### Post by jerrrys on 2010-01-17
colud you post a screen shot of your repository software sources

---

### Post by Daedalus.Maelstrom on 2010-01-20
Do you mean like this?

ajcote@Blue:~$ sudo apt-get update
[sudo] password for ajcote: 
Building old list of packages... [done]
Building old list of available updates... [done]
Building old list of watched packages... [done]
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release.gpg
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic Release
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]            
Get:2 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [189B]                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg [189B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Get:4 [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg [827B]               
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_US            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]              
Get:6 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,347B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg [189B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Get:8 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US       
Get:10 [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release [7,235B]                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release [44.1kB]            
Get:12 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [3,411B]           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Get:13 [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages [34.2kB]         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [49.2kB]       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Sources                          
Get:15 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources [1,385B]            
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release [37.1kB]          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages                   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [21.1kB]   
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages [142kB]       
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages [14B]   
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages [87.2kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages [65.7kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages [14B] 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages [13.6kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages [14B] 
Fetched 570kB in 1min 25s (6,644B/s)                                           
W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
ajcote@Blue:~$

---

### Post by Daedalus.Maelstrom on 2010-02-09
Thanks anyway, I've since reloaded the system and manually input the 'GetDeb' and 'PlayDeb' repositories into the software sources and have since had no problems with Synaptic.

---

