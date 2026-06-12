---
title: "synaptic problems"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by chudder on 2009-11-29
Hi,
I just started having problems with synaptic.  I found similar problems on other threads but they weren't quite the same and i tried all the remedies and none of them worked.  It is very possible I missed a couple too.  here is my output when I type sudo apt-get update.

I've switched servers, I've reimported the GPG key and I still get the same result.

Any help would be appreciated, thanks

Chud



```
chud@Lappy30X6:~$ sudo apt-get update
[sudo] password for chud: 
Get:1 http://mirrors.us.kernel.org jaunty Release.gpg [189B]
Ign http://mirrors.us.kernel.org jaunty/main Translation-en_US                 
Ign http://mirrors.us.kernel.org jaunty/restricted Translation-en_US           
Ign http://mirrors.us.kernel.org jaunty/universe Translation-en_US             
Ign http://mirrors.us.kernel.org jaunty/multiverse Translation-en_US           
Get:2 http://archive.canonical.com jaunty Release.gpg [189B]                   
Get:3 http://mirrors.us.kernel.org jaunty-updates Release.gpg [189B]           
Get:4 http://packages.medibuntu.org jaunty Release.gpg [197B]                  
Ign http://mirrors.us.kernel.org jaunty-updates/main Translation-en_US         
Get:5 http://wine.budgetdedicated.com jaunty Release.gpg [189B]                
Get:6 http://winff.org jaunty Release.gpg [197B]                               
Ign http://mirrors.us.kernel.org jaunty-updates/restricted Translation-en_US   
Ign http://mirrors.us.kernel.org jaunty-updates/universe Translation-en_US     
Ign http://archive.canonical.com jaunty/partner Translation-en_US              
Ign http://mirrors.us.kernel.org jaunty-updates/multiverse Translation-en_US   
Ign http://packages.medibuntu.org jaunty/free Translation-en_US                
Get:7 http://mirrors.us.kernel.org jaunty-security Release.gpg [189B]          
Ign http://wine.budgetdedicated.com jaunty/main Translation-en_US              
Ign http://winff.org jaunty/universe Translation-en_US                         
Ign http://mirrors.us.kernel.org jaunty-security/main Translation-en_US        
Ign http://mirrors.us.kernel.org jaunty-security/restricted Translation-en_US  
Get:8 http://archive.canonical.com jaunty Release [10.5kB]                     
Ign http://mirrors.us.kernel.org jaunty-security/universe Translation-en_US    
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US            
Ign http://archive.canonical.com jaunty Release                                
Ign http://mirrors.us.kernel.org jaunty-security/multiverse Translation-en_US  
Get:9 http://wine.budgetdedicated.com jaunty Release [1019B]                   
Get:10 http://winff.org jaunty Release [2037B]                                 
Ign http://wine.budgetdedicated.com jaunty Release                             
Ign http://winff.org jaunty Release                                            
Get:11 http://packages.medibuntu.org jaunty Release [11.7kB]                   
Ign http://packages.medibuntu.org jaunty Release                               
Hit http://archive.canonical.com jaunty/partner Packages                       
Ign http://wine.budgetdedicated.com jaunty/main Packages                       
Get:12 http://mirrors.us.kernel.org jaunty Release [74.6kB]                    
Hit http://winff.org jaunty/universe Packages                                  
Hit http://archive.canonical.com jaunty/partner Sources                        
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://wine.budgetdedicated.com jaunty/main Packages                       
Get:13 http://mirrors.us.kernel.org jaunty-updates Release [57.9kB]  
Get:14 http://mirrors.us.kernel.org jaunty-security Release [57.9kB]
Hit http://packages.medibuntu.org jaunty/non-free Packages                   
Get:15 http://mirrors.us.kernel.org jaunty/main Packages [1253kB]              
Hit http://packages.medibuntu.org jaunty/free Sources
Hit http://packages.medibuntu.org jaunty/non-free Sources
Get:16 http://mirrors.us.kernel.org jaunty/restricted Packages [8848B]
Get:17 http://mirrors.us.kernel.org jaunty/main Sources [555kB]
Get:18 http://mirrors.us.kernel.org jaunty/restricted Sources [3156B]
Get:19 http://mirrors.us.kernel.org jaunty/universe Packages [4757kB]
Get:20 http://mirrors.us.kernel.org jaunty/universe Sources [2375kB]           
Get:21 http://mirrors.us.kernel.org jaunty/multiverse Packages [197kB]         
Get:22 http://mirrors.us.kernel.org jaunty/multiverse Sources [107kB]          
Get:23 http://mirrors.us.kernel.org jaunty-updates/main Packages [210kB]       
Get:24 http://mirrors.us.kernel.org jaunty-updates/restricted Packages [2599B] 
Get:25 http://mirrors.us.kernel.org jaunty-updates/main Sources [58.6kB]       
Get:26 http://mirrors.us.kernel.org jaunty-updates/restricted Sources [509B]   
Get:27 http://mirrors.us.kernel.org jaunty-updates/universe Packages [90.8kB]  
Get:28 http://mirrors.us.kernel.org jaunty-updates/universe Sources [24.9kB]   
Get:29 http://mirrors.us.kernel.org jaunty-updates/multiverse Packages [8128B] 
Get:30 http://mirrors.us.kernel.org jaunty-updates/multiverse Sources [2505B]  
Get:31 http://mirrors.us.kernel.org jaunty-security/main Packages [122kB]      
Get:32 http://mirrors.us.kernel.org jaunty-security/restricted Packages [2599B]
Get:33 http://mirrors.us.kernel.org jaunty-security/main Sources [32.1kB]      
Get:34 http://mirrors.us.kernel.org jaunty-security/restricted Sources [509B]  
Get:35 http://mirrors.us.kernel.org jaunty-security/universe Packages [62.8kB] 
Get:36 http://mirrors.us.kernel.org jaunty-security/universe Sources [15.2kB]  
Get:37 http://mirrors.us.kernel.org jaunty-security/multiverse Packages [1662B]
Get:38 http://mirrors.us.kernel.org jaunty-security/multiverse Sources [588B]  
Fetched 10.1MB in 19s (528kB/s)                                                
Reading package lists... Done
W: GPG error: http://archive.canonical.com jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://wine.budgetdedicated.com jaunty Release: The following signatures were invalid: BADSIG 58403026387EE263 Scott Ritchie <scott@open-vote.org>
W: GPG error: http://winff.org jaunty Release: The following signatures were invalid: BADSIG 1CD52D7BAAFE086A Paul Gevers <paul.gevers@esac.climbing.nl>
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>
W: You may want to run apt-get update to correct these problems

```

---

### Post by chudder on 2009-11-29
Solved

---

