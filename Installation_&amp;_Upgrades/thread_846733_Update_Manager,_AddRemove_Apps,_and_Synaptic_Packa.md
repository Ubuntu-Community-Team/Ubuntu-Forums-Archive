---
title: "Update Manager, Add/Remove Apps, and Synaptic Package Manager don't work"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by tuguldur.o on 2008-07-01
I recently installed 7.10 on my Gateway laptop and updated it. Then all of a sudden, I couldn't Add/Remove applications and update anymore. When I try to update with the terminal, I get this:


togo@Togo-Ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release [58.5kB]     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [189B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release [44.0kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages [73.8kB]
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
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages [101kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages [98.5kB]   
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages [30.8kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages [17.0kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages [5779B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages [4847B]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources [11.5kB]     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources [19.3kB]         
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages [14B]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources [24.6kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources [9324B]          
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources [812B]     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources [944B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources [3659B]    
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources [14B]
Fetched 504kB in 2s (218kB/s)                      
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_gutsy_universe_binary-amd64_Packages (1)
E: The package lists or status file could not be parsed or opened.





Please help! I love Ubuntu, I don't want this to stop me from using it.

---

### Post by Partyboi2 on 2008-07-01
try changing the download  server (System>Admin>Software Sources>First tab)

---

### Post by tuguldur.o on 2008-07-01
That seems to have fixed the problem. I just changed the main server to the Server for United States. Thank you so much!!!

---

### Post by Partyboi2 on 2008-07-01
Your welcome :)

---

