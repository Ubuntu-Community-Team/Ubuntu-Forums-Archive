---
title: "apt-get update problems"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Jaysu on 2007-05-16
I looked around for some time, but can't get this problem figured out. When I type 

apt-get update

I get this response:
(skipping some lines)
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

Any ideas? Thanks.

---

### Post by heimo on 2007-05-16
> **Jaysu said:**
> Any ideas? Thanks.

Try Automatix support forums at
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Jaysu on 2007-05-16
Actually, I think the problem is even bigger than automatix. I tried to install ubuntu-desktop, and I've just had problems from there. Here is what I get when I run apt-get update...

# apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1) edgy/restricted Translation-en_US
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release.gpg [189B]                      
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Translation-en_US                    
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]        
Ign [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Translation-en_US      
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US        
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release [50.9kB]                
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Get:6 [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release [6733B]                         
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US            
Ign [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release                     
Hit [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages                             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US        
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release.gpg [191B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Translation-en_US       
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages                
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages [3786B]    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release                             
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release [50.9kB]                
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [40.8kB]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages                 
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/main Packages [81.4kB]          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages [5678B]     
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages [40.8kB]      
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages [3786B]     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                         
Get:20 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US                
Get:21 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release.gpg [191B]                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Translation-en_US                        
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release                               
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy Release                                       
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) edgy/main Packages                                 
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages                         
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Fetched 286kB in 11s (25.7kB/s)                                                
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: Unknown error executing gpgv
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://www.getautomatix.com](http://www.getautomatix.com) edgy/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_edgy_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@upenguin:~#

---

