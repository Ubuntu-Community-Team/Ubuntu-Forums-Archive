---
title: "Impossible to Update my PC"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by IL TRIVELLA on 2011-10-21
Hello everybody, 

since one month, everytime that I try to do the upgrades for my pc, after a bit that is charging the updates, I receive this message of error, I try and try, but nothing change, what can I do? thanks a lot...

[CENTER]```
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.3+dfsg-5ubuntu2.2_amd64.deb Connection failed [IP: 91.189.92.167 80]
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread-common_9.4.2.0-0natty1_all.deb Connection failed [IP: 91.189.92.191 80]
Failed to fetch http://archive.canonical.com/ubuntu/pool/partner/a/acroread/acroread_9.4.2.0-0natty1_amd64.deb Connection failed [IP: 91.189.92.191 80]

```[/CENTER]

---

### Post by raja.genupula on 2011-10-21
Open Update manager -> settings -> change your server to other and do update again

```
sudo apt-get update
``` and let me know what you got.

All The best.

---

### Post by IL TRIVELLA on 2011-10-21
> **raja.genupula said:**
> Open Update manager -> settings -> change your server to other and do update again

```
sudo apt-get update
``` and let me know what you got.

All The best.

ok I did the updates, but cannot do the update for the new version, I wait for more then one hour and then stops, and I try to search again updates but stops even this, say that he cannot find the info of the repository or something like this...

---

### Post by 23dornot23d on 2011-10-21
can you show us this list .... 

gedit /etc/apt/sources.list

copy and paste what you see and put between code tags if you could please .

---

### Post by raja.genupula on 2011-10-21
> **IL TRIVELLA said:**
> ok I did the updates, but cannot do the update for the new version, I wait for more then one hour and then stops, and I try to search again updates but stops even this, say that he cannot find the info of the repository or something like this...
Hi man 
please copy and paste here , what ever you got .We need that information also.

---

### Post by IL TRIVELLA on 2011-10-21
the problem is that my copy of Ubuntu is in Italian, but I will copy for you:

this is what I get if in the terminal I write the command *sudo apt-get update*:

```
alessandro@Alessandro:~$ sudo apt-get update
[sudo] password for alessandro: 
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick InRelease
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick Release.gpg
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick Release
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main TranslationIndex
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted TranslationIndex
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main amd64 Packages
  Usare apt-cdrom per far riconoscere questo CD-ROM da APT. apt-get update non può essere usato per aggiungere nuovi CD-ROM
Err cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted amd64 Packages
  Usare apt-cdrom per far riconoscere questo CD-ROM da APT. apt-get update non può essere usato per aggiungere nuovi CD-ROM
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main Translation-it_IT
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main Translation-it
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted Translation-it_IT
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted Translation-it
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007) maverick/restricted Translation-en
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://archive.canonical.com natty InRelease                               
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://it.archive.ubuntu.com maverick-backports InRelease                  
Trovato http://extras.ubuntu.com natty Release.gpg                             
Trovato http://it.archive.ubuntu.com maverick-backports Release.gpg            
Trovato http://ppa.launchpad.net natty Release.gpg                             
Trovato http://ppa.launchpad.net natty Release.gpg                             
Trovato http://archive.canonical.com natty Release.gpg                         
Trovato http://extras.ubuntu.com natty Release                                 
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Ign http://archive.ubuntu.com natty-security InRelease                         
Trovato http://it.archive.ubuntu.com maverick-backports Release                
Trovato http://ppa.launchpad.net natty Release.gpg                             
Trovato http://ppa.launchpad.net natty Release.gpg                             
Trovato http://ppa.launchpad.net natty Release.gpg                             
Ign http://ppa.launchpad.net natty Release.gpg                                 
Trovato http://archive.canonical.com natty Release                             
Trovato http://archive.ubuntu.com natty Release.gpg                            
Trovato http://it.archive.ubuntu.com maverick-backports/main Sources           
Trovato http://extras.ubuntu.com natty/main Sources                            
Trovato http://archive.ubuntu.com natty-updates Release.gpg                    
Trovato http://ppa.launchpad.net natty Release.gpg                             
Scaricamento di:1 http://archive.canonical.com natty/partner Sources [4178 B]  
99% [1 Sources bzip2 0 B] [In attesa degli header] [In attesa degli header] [Inbzip2: (stdin) is not a bzip2 file.
Trovato http://it.archive.ubuntu.com maverick-backports/restricted Sources     
Trovato http://it.archive.ubuntu.com maverick-backports/universe Sources       
Trovato http://it.archive.ubuntu.com maverick-backports/multiverse Sources     
Trovato http://it.archive.ubuntu.com maverick-backports/main amd64 Packages    
Trovato http://it.archive.ubuntu.com maverick-backports/restricted amd64 Packages
Trovato http://it.archive.ubuntu.com maverick-backports/universe amd64 Packages
Trovato http://it.archive.ubuntu.com maverick-backports/multiverse amd64 Packages
Ign http://it.archive.ubuntu.com maverick-backports/main TranslationIndex      
Ign http://it.archive.ubuntu.com maverick-backports/multiverse TranslationIndex
Trovato http://archive.ubuntu.com natty-security Release.gpg                   
Ign http://it.archive.ubuntu.com maverick-backports/restricted TranslationIndex
Trovato http://extras.ubuntu.com natty/main amd64 Packages                     
Trovato http://ppa.launchpad.net natty Release                                 
Trovato http://ppa.launchpad.net natty Release                                 
Trovato http://ppa.launchpad.net natty Release                                 
Trovato http://ppa.launchpad.net natty Release                                 
Trovato http://ppa.launchpad.net natty Release                                 
Ign http://it.archive.ubuntu.com maverick-backports/universe TranslationIndex  
Ign http://archive.canonical.com natty/partner TranslationIndex                
Trovato http://archive.ubuntu.com natty Release                                
Ign http://ppa.launchpad.net natty Release                                     
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty-updates Release                        
Trovato http://ppa.launchpad.net natty Release                                 
Scaricamento di:2 http://archive.canonical.com natty/partner amd64 Packages [8912 B]
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty-security Release                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty/main Sources                           
Trovato http://archive.ubuntu.com natty/restricted Sources                     
Trovato http://archive.ubuntu.com natty/universe Sources                       
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty/multiverse Sources                     
Trovato http://archive.ubuntu.com natty/main amd64 Packages                    
Trovato http://archive.ubuntu.com natty/restricted amd64 Packages              
Trovato http://archive.ubuntu.com natty/universe amd64 Packages                
Trovato http://archive.ubuntu.com natty/multiverse amd64 Packages              
Trovato http://ppa.launchpad.net natty/main Sources                            
Trovato http://ppa.launchpad.net natty/main amd64 Packages                     
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Err http://archive.canonical.com natty/partner Sources                         
  404  Not Found [IP: 91.189.92.191 80]
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Trovato http://archive.ubuntu.com natty-updates/main Sources                   
Trovato http://archive.ubuntu.com natty-updates/restricted Sources             
Trovato http://archive.ubuntu.com natty-updates/universe Sources               
Trovato http://archive.ubuntu.com natty-updates/multiverse Sources             
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty-updates/main amd64 Packages            
Trovato http://archive.ubuntu.com natty-updates/restricted amd64 Packages      
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Trovato http://archive.ubuntu.com natty-updates/universe amd64 Packages        
Trovato http://archive.ubuntu.com natty-updates/multiverse amd64 Packages      
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Scaricamento di:3 http://ppa.launchpad.net natty/main Sources [3412 B]         
Scaricamento di:4 http://ppa.launchpad.net natty/main amd64 Packages [9528 B]  
Trovato http://archive.ubuntu.com natty-security/main Sources                  
Trovato http://archive.ubuntu.com natty-security/restricted Sources            
Trovato http://archive.ubuntu.com natty-security/universe Sources              
Trovato http://archive.ubuntu.com natty-security/multiverse Sources            
Trovato http://archive.ubuntu.com natty-security/main amd64 Packages           
Trovato http://archive.ubuntu.com natty-security/restricted amd64 Packages     
Trovato http://archive.ubuntu.com natty-security/universe amd64 Packages       
Trovato http://archive.ubuntu.com natty-security/multiverse amd64 Packages     
Ign http://archive.ubuntu.com natty-security/main TranslationIndex             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex       
Ign http://it.archive.ubuntu.com maverick-backports/main Translation-it_IT     
Ign http://it.archive.ubuntu.com maverick-backports/main Translation-it        
Ign http://it.archive.ubuntu.com maverick-backports/main Translation-en        
Ign http://it.archive.ubuntu.com maverick-backports/multiverse Translation-it_IT
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex         
Ign http://it.archive.ubuntu.com maverick-backports/multiverse Translation-it  
Ign http://it.archive.ubuntu.com maverick-backports/multiverse Translation-en  
Ign http://it.archive.ubuntu.com maverick-backports/restricted Translation-it_IT
Trovato http://archive.ubuntu.com natty/main Translation-it                    
Trovato http://archive.ubuntu.com natty/multiverse Translation-it              
Trovato http://archive.ubuntu.com natty/restricted Translation-it              
Ign http://it.archive.ubuntu.com maverick-backports/restricted Translation-it  
Ign http://it.archive.ubuntu.com maverick-backports/restricted Translation-en  
Ign http://it.archive.ubuntu.com maverick-backports/universe Translation-it_IT 
Ign http://it.archive.ubuntu.com maverick-backports/universe Translation-it    
Ign http://it.archive.ubuntu.com maverick-backports/universe Translation-en    
Trovato http://archive.ubuntu.com natty/universe Translation-it                
Scaricamento di:5 http://ppa.launchpad.net natty/main amd64 Packages [7069 B]  
Ign http://extras.ubuntu.com natty/main Translation-it_IT                      
Scaricamento di:6 http://ppa.launchpad.net natty/main Sources [6950 B]         
Scaricamento di:7 http://ppa.launchpad.net natty/main amd64 Packages [25,6 kB] 
Ign http://archive.canonical.com natty/partner Translation-it_IT               
Ign http://extras.ubuntu.com natty/main Translation-it                         
Ign http://archive.canonical.com natty/partner Translation-it                 
Ign http://extras.ubuntu.com natty/main Translation-en                        
Scaricamento di:8 http://ppa.launchpad.net natty/main Sources [1066 B]        
Scaricamento di:9 http://ppa.launchpad.net natty/main amd64 Packages [1617 B]  
Ign http://archive.canonical.com natty/partner Translation-en                  
Scaricamento di:10 http://ppa.launchpad.net natty/main Sources [5537 B]       
Scaricamento di:11 http://ppa.launchpad.net natty/main amd64 Packages [12,5 kB]
Scaricamento di:12 http://ppa.launchpad.net natty/main Sources [8132 B]     
Err http://ppa.launchpad.net natty/main Sources      
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-it_IT
Ign http://ppa.launchpad.net natty/main Translation-it
Ign http://ppa.launchpad.net natty/main Translation-en
Ign http://ppa.launchpad.net natty/main Translation-it_IT
Ign http://ppa.launchpad.net natty/main Translation-it
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-it_IT                      
Ign http://ppa.launchpad.net natty/main Translation-it                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-it_IT                      
Ign http://ppa.launchpad.net natty/main Translation-it                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-it_IT                      
Ign http://ppa.launchpad.net natty/main Translation-it                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-it_IT                      
Ign http://ppa.launchpad.net natty/main Translation-it                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://ppa.launchpad.net natty/main Translation-it_IT                      
Ign http://ppa.launchpad.net natty/main Translation-it                         
Ign http://ppa.launchpad.net natty/main Translation-en                         
Ign http://archive.ubuntu.com natty/main Translation-it_IT                     
Ign http://archive.ubuntu.com natty/main Translation-en                        
Ign http://archive.ubuntu.com natty/multiverse Translation-it_IT               
Ign http://archive.ubuntu.com natty/multiverse Translation-en                  
Ign http://archive.ubuntu.com natty/restricted Translation-it_IT               
Ign http://archive.ubuntu.com natty/restricted Translation-en                  
Ign http://archive.ubuntu.com natty/universe Translation-it_IT                 
Ign http://archive.ubuntu.com natty/universe Translation-en                    
Ign http://archive.ubuntu.com natty-updates/main Translation-it_IT             
Ign http://archive.ubuntu.com natty-updates/main Translation-it                
Ign http://archive.ubuntu.com natty-updates/main Translation-en                
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-it_IT       
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-it          
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-it_IT       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-it          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en          
Ign http://archive.ubuntu.com natty-updates/universe Translation-it_IT         
Ign http://archive.ubuntu.com natty-updates/universe Translation-it            
Ign http://archive.ubuntu.com natty-updates/universe Translation-en            
Ign http://archive.ubuntu.com natty-security/main Translation-it_IT            
Ign http://archive.ubuntu.com natty-security/main Translation-it               
Ign http://archive.ubuntu.com natty-security/main Translation-en               
Ign http://archive.ubuntu.com natty-security/multiverse Translation-it_IT      
Ign http://archive.ubuntu.com natty-security/multiverse Translation-it         
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en         
Ign http://archive.ubuntu.com natty-security/restricted Translation-it_IT      
Ign http://archive.ubuntu.com natty-security/restricted Translation-it         
Ign http://archive.ubuntu.com natty-security/restricted Translation-en         
Ign http://archive.ubuntu.com natty-security/universe Translation-it_IT        
Ign http://archive.ubuntu.com natty-security/universe Translation-it           
Ign http://archive.ubuntu.com natty-security/universe Translation-en           
Recuperati 12 B in 7s (2 B/s)                                                  
W: Impossibile recuperare cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/main/binary-amd64/Packages  Usare apt-cdrom per far riconoscere questo CD-ROM da APT. apt-get update non può essere usato per aggiungere nuovi CD-ROM

W: Impossibile recuperare cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/restricted/binary-amd64/Packages  Usare apt-cdrom per far riconoscere questo CD-ROM da APT. apt-get update non può essere usato per aggiungere nuovi CD-ROM

W: Impossibile recuperare http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources  404  Not Found [IP: 91.189.92.191 80]

W: Impossibile recuperare gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_awn-testing_ppa_ubuntu_dists_natty_main_source_Sources  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_awn-testing_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Somma hash non corrispondente

W: Impossibile recuperare gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bisigi_ppa_ubuntu_dists_natty_main_source_Sources  Somma hash non corrispondente

W: Impossibile recuperare gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bisigi_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_mixxx_mixxx_ubuntu_dists_natty_main_source_Sources  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_mixxx_mixxx_ubuntu_dists_natty_main_binary-amd64_Packages  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_source_Sources  Somma hash non corrispondente

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Somma hash non corrispondente

W: Impossibile recuperare http://ppa.launchpad.net/ubuntu-wine/ppa./ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Impossibile recuperare http://ppa.launchpad.net/ubuntu-wine/ppa./ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Impossibile recuperare copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_natty_main_source_Sources  Somma hash non corrispondente

W: Impossibile recuperare gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_natty_main_binary-amd64_Packages  Somma hash non corrispondente

E: Impossibile scaricare alcuni file di indice: saranno ignorati o verranno usati quelli vecchi.
alessandro@Alessandro:~$ 

```

as you can see, I can't do even this, then if I do the command *gedit /etc/apt/sources.list* I get this:

```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://it.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://it.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse
```

this instead is what I get if I try to just check for updates, the message of error say "Downloading repository information failed":

```
W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)/dists/maverick/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://archive.canonical.com/ubuntu/dists/natty/partner/source/Sources  404  Not Found [IP: 91.189.88.33 80]
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_natty_partner_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_awn-testing_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_awn-testing_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bisigi_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_bisigi_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_mixxx_mixxx_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_mixxx_mixxx_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-wine_ppa_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, W:Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa./ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa./ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_natty_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch gzip:/var/lib/apt/lists/partial/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_natty_main_binary-amd64_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

so what is mean? where is the problem?

---

### Post by 23dornot23d on 2011-10-21
It is trying to find the  files off the cdrom ....

obviously its not in the drive ...... but if you comment out line one  ....

So the first line by adding a hash before it ....

#

so it looks like the line below in red

It will stop it looking there .....

sudo gedit /apt/etc/sources.list

[COLOR=Red]#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted[/COLOR]

leave the rest as is


Then save ...... ctrl+s or pick it in the top left to save .....

then once saved and out of the editor ...  do

sudo apt-get update

---

### Post by IL TRIVELLA on 2011-10-21
> **23dornot23d said:**
> It is trying to find the  files off the cdrom ....

obviously its not in the drive ...... but if you comment out line one  ....

So the first line by adding a hash before it ....

#

so it looks like the line below in red

It will stop it looking there .....

sudo gedit /apt/etc/sources.list

[COLOR=Red]#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted[/COLOR]

leave the rest as is


Then save ...... ctrl+s or pick it in the top left to save .....

then once saved and out of the editor ...  do

sudo apt-get update

I did it and now when I do sudo apt-get update:

```
alessandro@Alessandro:~$ sudo apt-get update
[sudo] password for alessandro: 
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://it.archive.ubuntu.com maverick-backports InRelease        
Hit http://extras.ubuntu.com oneiric Release                         
Ign http://archive.ubuntu.com oneiric InRelease                      
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-security InRelease             
Hit http://archive.canonical.com oneiric Release                     
Hit http://it.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://it.archive.ubuntu.com maverick-backports Release          
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/main Sources               
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex    
Hit http://archive.ubuntu.com oneiric-security Release.gpg           
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages        
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://it.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://it.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages       
Hit http://archive.ubuntu.com oneiric/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex    
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Sources
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://archive.ubuntu.com oneiric-updates/universe Sources       
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources     
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/main Sources          
Hit http://archive.ubuntu.com oneiric-security/restricted Sources    
Hit http://archive.ubuntu.com oneiric-security/universe Sources      
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages   
Hit http://archive.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB          
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://archive.canonical.com oneiric/partner Translation-en_GB   
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-it             
Ign http://archive.canonical.com oneiric/partner Translation-en
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/main Translation-it
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-it
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-it
Ign http://archive.canonical.com oneiric/partner Translation-it
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-it
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
Fetched 72 B in 4s (15 B/s)
Reading package lists... Done
alessandro@Alessandro:~$ 

```

and then when I go on Update manager don't say more error, but is also true that at the moment there is nothing to update, but before even when I was checking stops for the error, seems be good now...

---

### Post by 23dornot23d on 2011-10-21
Good to hear ,,, ;)

---

### Post by IL TRIVELLA on 2011-10-22
> **23dornot23d said:**
> Good to hear ,,, ;)

I hope stay like this, thanks everybody for the help, if in any case in the next update will give me problems I will post again here...

---

### Post by IL TRIVELLA on 2011-10-24
I've again a problem to update, if from terminal I give the command "*sudo apt-get update*" happen this:

```
alessandro@Alessandro:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://it.archive.ubuntu.com maverick-backports InRelease                  
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://it.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports Release                    
Hit http://archive.ubuntu.com oneiric Release                                  
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports/main Sources               
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://it.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources               
Hit http://archive.ubuntu.com oneiric-updates/universe Sources                 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources     
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages    
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources                
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources    
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages             
Hit http://archive.ubuntu.com oneiric-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB         
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://archive.ubuntu.com oneiric/main Translation-it                      
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-it                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB   
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/multiverse Translation-it                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric/restricted Translation-it                
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB               
Hit http://archive.ubuntu.com oneiric/universe Translation-en        
Hit http://archive.ubuntu.com oneiric/universe Translation-it        
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-it                
Ign http://ppa.launchpad.net oneiric/main Translation-it                       
Ign http://extras.ubuntu.com oneiric/main Translation-it             
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
alessandro@Alessandro:~$ 

```

---

### Post by raja.genupula on 2011-10-25
> **IL TRIVELLA said:**
> I've again a problem to update, if from terminal I give the command "*sudo apt-get update*" happen this:

```
alessandro@Alessandro:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://archive.canonical.com oneiric Release.gpg                           
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://it.archive.ubuntu.com maverick-backports InRelease                  
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Ign http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://extras.ubuntu.com oneiric/main Sources                              
Ign http://ppa.launchpad.net oneiric Release                                   
Hit http://it.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports Release                    
Hit http://archive.ubuntu.com oneiric Release                                  
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports/main Sources               
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://it.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex          
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources               
Hit http://archive.ubuntu.com oneiric-updates/universe Sources                 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources     
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages    
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages           
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources                
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources    
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages             
Hit http://archive.ubuntu.com oneiric-security/restricted amd64 Packages       
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en_GB         
Hit http://archive.ubuntu.com oneiric/main Translation-en            
Hit http://archive.ubuntu.com oneiric/main Translation-it                      
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Ign http://ppa.launchpad.net oneiric/main Translation-en             
Ign http://ppa.launchpad.net oneiric/main Translation-it                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en_GB   
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://archive.canonical.com oneiric/partner Translation-en                
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/multiverse Translation-it                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en_GB   
Hit http://archive.ubuntu.com oneiric/restricted Translation-en      
Hit http://archive.ubuntu.com oneiric/restricted Translation-it                
Hit http://archive.ubuntu.com oneiric/universe Translation-en_GB               
Hit http://archive.ubuntu.com oneiric/universe Translation-en        
Hit http://archive.ubuntu.com oneiric/universe Translation-it        
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-it                
Ign http://ppa.launchpad.net oneiric/main Translation-it                       
Ign http://extras.ubuntu.com oneiric/main Translation-it             
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
alessandro@Alessandro:~$ 

```

ok do this 

```
sudo rm -vf /var/lib/apt/lists/* 
sudo apt-get update 
```

all the best.

---

### Post by IL TRIVELLA on 2011-10-25
> **raja.genupula said:**
> ok do this 

```
sudo rm -vf /var/lib/apt/lists/* 
sudo apt-get update 
```all the best.


did it, everything is ok now?

```
alessandro@Alessandro:~$ sudo rm -vf /var/lib/apt/lists/*
[sudo] password for alessandro: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_main_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_Release'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_Release.gpg'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_Release.gpg'
alessandro@Alessandro:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                          
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                           
Get:1 http://archive.canonical.com oneiric Release.gpg [198 B]                                                                                                                 
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                  
Ign http://it.archive.ubuntu.com maverick-backports InRelease                                                             
Ign http://archive.ubuntu.com oneiric InRelease                                            
Ign http://archive.ubuntu.com oneiric-updates InRelease                                    
Ign http://archive.ubuntu.com oneiric-security InRelease                                   
Get:3 http://archive.canonical.com oneiric Release [5,922 B]                               
Ign http://ppa.launchpad.net oneiric Release.gpg                                                                           
Get:4 http://extras.ubuntu.com oneiric Release [9,759 B]                                   
Get:5 http://it.archive.ubuntu.com maverick-backports Release.gpg [198 B]                                                  
Get:6 http://archive.ubuntu.com oneiric Release.gpg [198 B]                                                                
Get:7 http://archive.canonical.com oneiric/partner Sources [1,847 B]                                                                  
Get:8 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                                                           
Get:9 http://it.archive.ubuntu.com maverick-backports Release [27.2 kB]                                                                          
Get:10 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]                                                    
Ign http://ppa.launchpad.net oneiric Release                                                                                           
Get:11 http://archive.canonical.com oneiric/partner amd64 Packages [3,125 B]                                               
Get:12 http://archive.canonical.com oneiric/partner i386 Packages [3,547 B]                                                                        
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                                                  
Get:13 http://extras.ubuntu.com oneiric/main Sources [14 B]                                                                                        
Get:14 http://archive.ubuntu.com oneiric-security Release.gpg [198 B]                                                                             
Get:15 http://ppa.launchpad.net oneiric Release [9,736 B]                                                                  
Get:16 http://archive.ubuntu.com oneiric Release [40.8 kB]                                                                            
Get:17 http://extras.ubuntu.com oneiric/main amd64 Packages [14 B]                                                                   
Get:18 http://extras.ubuntu.com oneiric/main i386 Packages [14 B]                                                                                             
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                            
Get:19 http://it.archive.ubuntu.com maverick-backports/main Sources [6,429 B]                                                                       
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                             
Get:20 http://ppa.launchpad.net oneiric/main Sources [694 B]                                                                
Get:21 http://ppa.launchpad.net oneiric/main amd64 Packages [737 B]                                                                                
Get:22 http://ppa.launchpad.net oneiric/main i386 Packages [744 B]                                                                                  
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                          
Get:23 http://it.archive.ubuntu.com maverick-backports/restricted Sources [14 B]                                                                    
Get:24 http://it.archive.ubuntu.com maverick-backports/universe Sources [8,968 B]                                                                  
Get:25 http://it.archive.ubuntu.com maverick-backports/multiverse Sources [14 B]                                                                   
Get:26 http://archive.ubuntu.com oneiric-updates Release [32.4 kB]             ]
Get:27 http://archive.ubuntu.com oneiric-security Release [28.2 kB]            
Get:28 http://archive.ubuntu.com oneiric/main Sources [877 kB]                 
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                      
  404  Not Found
Ign http://archive.canonical.com oneiric/partner Translation-en                
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:29 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]          
Get:30 http://archive.ubuntu.com oneiric/universe Sources [4,677 kB]           
Get:31 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]           
Get:32 http://archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]        
Get:33 http://archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]   
Get:34 http://archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]    
Get:35 http://archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]    
Get:36 http://archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]         
Get:37 http://archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]    
Get:38 http://archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]     
Get:39 http://archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]     
Get:40 http://archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]     
Get:41 http://archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]       
Get:42 http://archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B] 
Get:43 http://archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B] 
Get:44 http://archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]   
Get:45 http://archive.ubuntu.com oneiric-updates/main Sources [55.8 kB]        
Get:46 http://archive.ubuntu.com oneiric-updates/restricted Sources [14 B]     
Get:47 http://archive.ubuntu.com oneiric-updates/universe Sources [4,319 B]    
Get:48 http://archive.ubuntu.com oneiric-updates/multiverse Sources [1,032 B]  
Get:49 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [103 kB]  
Get:50 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [14 B]
Get:51 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [20.6 kB]
Get:52 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [2,698 B]
Get:53 http://archive.ubuntu.com oneiric-updates/main i386 Packages [103 kB]   
Get:54 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [14 B]
Get:55 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [20.9 kB]
Get:56 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [2,703 B]
Get:57 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]  
Get:58 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:59 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [70 B]
Get:60 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:61 http://archive.ubuntu.com oneiric-security/main Sources [4,229 B]       
Get:62 http://archive.ubuntu.com oneiric-security/restricted Sources [14 B]    
Get:63 http://archive.ubuntu.com oneiric-security/universe Sources [14 B]      
Get:64 http://archive.ubuntu.com oneiric-security/multiverse Sources [14 B]    
Get:65 http://archive.ubuntu.com oneiric-security/main amd64 Packages [10.5 kB]
Get:66 http://archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:67 http://archive.ubuntu.com oneiric-security/universe amd64 Packages [4,844 B]
Get:68 http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages [14 B]
Get:69 http://archive.ubuntu.com oneiric-security/main i386 Packages [10.5 kB] 
Get:70 http://archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:71 http://archive.ubuntu.com oneiric-security/universe i386 Packages [4,851 B]
Get:72 http://archive.ubuntu.com oneiric-security/multiverse i386 Packages [14 B]
Get:73 http://archive.ubuntu.com oneiric-security/main TranslationIndex [72 B] 
Get:74 http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex [70 B]
Get:75 http://archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:76 http://archive.ubuntu.com oneiric-security/universe TranslationIndex [72 B]
Get:77 http://archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]      
Get:78 http://archive.ubuntu.com oneiric/main Translation-en [701 kB]          
Get:79 http://archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB]
Get:80 http://archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]   
Get:81 http://archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B]
Get:82 http://archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]   
Get:83 http://archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]  
Get:84 http://archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]    
Get:85 http://archive.ubuntu.com oneiric-updates/main Translation-en [53.5 kB] 
Get:86 http://archive.ubuntu.com oneiric-updates/multiverse Translation-en [1,190 B]
Get:87 http://archive.ubuntu.com oneiric-updates/restricted Translation-en [14 B]
Get:88 http://archive.ubuntu.com oneiric-updates/universe Translation-en [14.0 kB]
Get:89 http://archive.ubuntu.com oneiric-security/main Translation-en [6,757 B]
Get:90 http://archive.ubuntu.com oneiric-security/multiverse Translation-en [14 B]
Get:91 http://archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]
Get:92 http://archive.ubuntu.com oneiric-security/universe Translation-en [3,784 B]
Fetched 21.4 MB in 9min 4s (39.3 kB/s)                                         
W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
alessandro@Alessandro:~$ 

```

and if I try to update from Update Manager stop for error and in the details I got this:

```
W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by raja.genupula on 2011-10-25
> **IL TRIVELLA said:**
> did it, everything is ok now?

```
alessandro@Alessandro:~$ sudo rm -vf /var/lib/apt/lists/*
[sudo] password for alessandro: 
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_oneiric_Release.gpg'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_main_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_Release'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_Release.gpg'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_maverick-backports_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_tiheum_equinox_ubuntu_dists_oneiric_Release.gpg'
alessandro@Alessandro:~$ sudo apt-get update
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                          
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                           
Get:1 http://archive.canonical.com oneiric Release.gpg [198 B]                                                                                                                 
Ign http://ppa.launchpad.net oneiric InRelease                                                                                                                                 
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                  
Ign http://it.archive.ubuntu.com maverick-backports InRelease                                                             
Ign http://archive.ubuntu.com oneiric InRelease                                            
Ign http://archive.ubuntu.com oneiric-updates InRelease                                    
Ign http://archive.ubuntu.com oneiric-security InRelease                                   
Get:3 http://archive.canonical.com oneiric Release [5,922 B]                               
Ign http://ppa.launchpad.net oneiric Release.gpg                                                                           
Get:4 http://extras.ubuntu.com oneiric Release [9,759 B]                                   
Get:5 http://it.archive.ubuntu.com maverick-backports Release.gpg [198 B]                                                  
Get:6 http://archive.ubuntu.com oneiric Release.gpg [198 B]                                                                
Get:7 http://archive.canonical.com oneiric/partner Sources [1,847 B]                                                                  
Get:8 http://ppa.launchpad.net oneiric Release.gpg [316 B]                                                                           
Get:9 http://it.archive.ubuntu.com maverick-backports Release [27.2 kB]                                                                          
Get:10 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]                                                    
Ign http://ppa.launchpad.net oneiric Release                                                                                           
Get:11 http://archive.canonical.com oneiric/partner amd64 Packages [3,125 B]                                               
Get:12 http://archive.canonical.com oneiric/partner i386 Packages [3,547 B]                                                                        
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                                                  
Get:13 http://extras.ubuntu.com oneiric/main Sources [14 B]                                                                                        
Get:14 http://archive.ubuntu.com oneiric-security Release.gpg [198 B]                                                                             
Get:15 http://ppa.launchpad.net oneiric Release [9,736 B]                                                                  
Get:16 http://archive.ubuntu.com oneiric Release [40.8 kB]                                                                            
Get:17 http://extras.ubuntu.com oneiric/main amd64 Packages [14 B]                                                                   
Get:18 http://extras.ubuntu.com oneiric/main i386 Packages [14 B]                                                                                             
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                            
Get:19 http://it.archive.ubuntu.com maverick-backports/main Sources [6,429 B]                                                                       
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                             
Get:20 http://ppa.launchpad.net oneiric/main Sources [694 B]                                                                
Get:21 http://ppa.launchpad.net oneiric/main amd64 Packages [737 B]                                                                                
Get:22 http://ppa.launchpad.net oneiric/main i386 Packages [744 B]                                                                                  
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                                                                                          
Get:23 http://it.archive.ubuntu.com maverick-backports/restricted Sources [14 B]                                                                    
Get:24 http://it.archive.ubuntu.com maverick-backports/universe Sources [8,968 B]                                                                  
Get:25 http://it.archive.ubuntu.com maverick-backports/multiverse Sources [14 B]                                                                   
Get:26 http://archive.ubuntu.com oneiric-updates Release [32.4 kB]             ]
Get:27 http://archive.ubuntu.com oneiric-security Release [28.2 kB]            
Get:28 http://archive.ubuntu.com oneiric/main Sources [877 kB]                 
Ign http://archive.canonical.com oneiric/partner Translation-en_GB             
Err http://ppa.launchpad.net oneiric/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net oneiric/main amd64 Packages                      
  404  Not Found
Ign http://archive.canonical.com oneiric/partner Translation-en                
Err http://ppa.launchpad.net oneiric/main i386 Packages                        
  404  Not Found
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:29 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]          
Get:30 http://archive.ubuntu.com oneiric/universe Sources [4,677 kB]           
Get:31 http://archive.ubuntu.com oneiric/multiverse Sources [149 kB]           
Get:32 http://archive.ubuntu.com oneiric/main amd64 Packages [1,226 kB]        
Get:33 http://archive.ubuntu.com oneiric/restricted amd64 Packages [8,261 B]   
Get:34 http://archive.ubuntu.com oneiric/universe amd64 Packages [4,460 kB]    
Get:35 http://archive.ubuntu.com oneiric/multiverse amd64 Packages [117 kB]    
Get:36 http://archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]         
Get:37 http://archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B]    
Get:38 http://archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]     
Get:39 http://archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]     
Get:40 http://archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]     
Get:41 http://archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]       
Get:42 http://archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B] 
Get:43 http://archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B] 
Get:44 http://archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]   
Get:45 http://archive.ubuntu.com oneiric-updates/main Sources [55.8 kB]        
Get:46 http://archive.ubuntu.com oneiric-updates/restricted Sources [14 B]     
Get:47 http://archive.ubuntu.com oneiric-updates/universe Sources [4,319 B]    
Get:48 http://archive.ubuntu.com oneiric-updates/multiverse Sources [1,032 B]  
Get:49 http://archive.ubuntu.com oneiric-updates/main amd64 Packages [103 kB]  
Get:50 http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages [14 B]
Get:51 http://archive.ubuntu.com oneiric-updates/universe amd64 Packages [20.6 kB]
Get:52 http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages [2,698 B]
Get:53 http://archive.ubuntu.com oneiric-updates/main i386 Packages [103 kB]   
Get:54 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [14 B]
Get:55 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [20.9 kB]
Get:56 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [2,703 B]
Get:57 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]  
Get:58 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:59 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [70 B]
Get:60 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:61 http://archive.ubuntu.com oneiric-security/main Sources [4,229 B]       
Get:62 http://archive.ubuntu.com oneiric-security/restricted Sources [14 B]    
Get:63 http://archive.ubuntu.com oneiric-security/universe Sources [14 B]      
Get:64 http://archive.ubuntu.com oneiric-security/multiverse Sources [14 B]    
Get:65 http://archive.ubuntu.com oneiric-security/main amd64 Packages [10.5 kB]
Get:66 http://archive.ubuntu.com oneiric-security/restricted amd64 Packages [14 B]
Get:67 http://archive.ubuntu.com oneiric-security/universe amd64 Packages [4,844 B]
Get:68 http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages [14 B]
Get:69 http://archive.ubuntu.com oneiric-security/main i386 Packages [10.5 kB] 
Get:70 http://archive.ubuntu.com oneiric-security/restricted i386 Packages [14 B]
Get:71 http://archive.ubuntu.com oneiric-security/universe i386 Packages [4,851 B]
Get:72 http://archive.ubuntu.com oneiric-security/multiverse i386 Packages [14 B]
Get:73 http://archive.ubuntu.com oneiric-security/main TranslationIndex [72 B] 
Get:74 http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex [70 B]
Get:75 http://archive.ubuntu.com oneiric-security/restricted TranslationIndex [70 B]
Get:76 http://archive.ubuntu.com oneiric-security/universe TranslationIndex [72 B]
Get:77 http://archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]      
Get:78 http://archive.ubuntu.com oneiric/main Translation-en [701 kB]          
Get:79 http://archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB]
Get:80 http://archive.ubuntu.com oneiric/multiverse Translation-en [92.6 kB]   
Get:81 http://archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B]
Get:82 http://archive.ubuntu.com oneiric/restricted Translation-en [2,229 B]   
Get:83 http://archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]  
Get:84 http://archive.ubuntu.com oneiric/universe Translation-en [3,165 kB]    
Get:85 http://archive.ubuntu.com oneiric-updates/main Translation-en [53.5 kB] 
Get:86 http://archive.ubuntu.com oneiric-updates/multiverse Translation-en [1,190 B]
Get:87 http://archive.ubuntu.com oneiric-updates/restricted Translation-en [14 B]
Get:88 http://archive.ubuntu.com oneiric-updates/universe Translation-en [14.0 kB]
Get:89 http://archive.ubuntu.com oneiric-security/main Translation-en [6,757 B]
Get:90 http://archive.ubuntu.com oneiric-security/multiverse Translation-en [14 B]
Get:91 http://archive.ubuntu.com oneiric-security/restricted Translation-en [14 B]
Get:92 http://archive.ubuntu.com oneiric-security/universe Translation-en [3,784 B]
Fetched 21.4 MB in 9min 4s (39.3 kB/s)                                         
W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
alessandro@Alessandro:~$ 

```and if I try to update from Update Manager stop for error and in the details I got this:

```
W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```


OK now open your update manager , click at settings and then at other software ,look for this three things and uncheck the checkboxe's then do the update again.

all the best.

---

### Post by IL TRIVELLA on 2011-10-25
> **raja.genupula said:**
> OK now open your update manager , click at settings and then at other software ,look for this three things and uncheck the checkboxe's then do the update again.

all the best.

I did it but I didn't found the voices that you mean, but similar, and only two, look: 

[http://imageshack.us/f/821/screenshotat20111025131.png/](http://imageshack.us/f/821/screenshotat20111025131.png/)

then I did check, and everything is ok, then I tryed on terminal and this is what I got, it is good right?

```
alessandro@Alessandro:~$ sudo apt-get update
[sudo] password for alessandro: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://it.archive.ubuntu.com maverick-backports InRelease                  
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://it.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports Release                    
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://it.archive.ubuntu.com maverick-backports/main Sources               
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://it.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://it.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources               
Hit http://archive.ubuntu.com oneiric-updates/universe Sources                 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources               
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages              
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages 
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources      
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources    
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages             
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages    
Ign http://archive.canonical.com oneiric/partner Translation-en_GB   
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://archive.canonical.com oneiric/partner Translation-en      
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Get:1 http://archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Get:2 http://archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB] 
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Get:3 http://archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B] 
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Get:4 http://archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]   
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Fetched 144 kB in 11s (12.2 kB/s)                                              
Reading package lists... Done
alessandro@Alessandro:~$ 

```

---

### Post by raja.genupula on 2011-10-25
> **IL TRIVELLA said:**
> I did it but I didn't found the voices that you mean, but similar, and only two, look: 

[http://imageshack.us/f/821/screenshotat20111025131.png/](http://imageshack.us/f/821/screenshotat20111025131.png/)

then I did check, and everything is ok, then I tryed on terminal and this is what I got, it is good right?

```
alessandro@Alessandro:~$ sudo apt-get update
[sudo] password for alessandro: 
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://it.archive.ubuntu.com maverick-backports InRelease                  
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease                        
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.canonical.com oneiric Release                               
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://archive.canonical.com oneiric/partner Sources                       
Hit http://archive.ubuntu.com oneiric-updates Release.gpg                      
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner amd64 Packages                
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://it.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric/main amd64 Packages                       
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://it.archive.ubuntu.com maverick-backports Release                    
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://it.archive.ubuntu.com maverick-backports/main Sources               
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources                       
Hit http://archive.ubuntu.com oneiric/main amd64 Packages                      
Hit http://archive.ubuntu.com oneiric/restricted amd64 Packages                
Hit http://archive.ubuntu.com oneiric/universe amd64 Packages                  
Hit http://archive.ubuntu.com oneiric/multiverse amd64 Packages                
Hit http://it.archive.ubuntu.com maverick-backports/restricted Sources         
Hit http://archive.ubuntu.com oneiric/main i386 Packages                       
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://it.archive.ubuntu.com maverick-backports/universe Sources           
Hit http://it.archive.ubuntu.com maverick-backports/multiverse Sources         
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex              
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex                
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources               
Hit http://archive.ubuntu.com oneiric-updates/universe Sources                 
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources               
Hit http://archive.ubuntu.com oneiric-updates/main amd64 Packages              
Hit http://archive.ubuntu.com oneiric-updates/restricted amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/universe amd64 Packages          
Hit http://archive.ubuntu.com oneiric-updates/multiverse amd64 Packages        
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages               
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages 
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages         
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex            
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources      
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources    
Hit http://archive.ubuntu.com oneiric-security/main amd64 Packages             
Ign http://extras.ubuntu.com oneiric/main Translation-en_GB                    
Hit http://archive.ubuntu.com oneiric-security/restricted amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages    
Ign http://archive.canonical.com oneiric/partner Translation-en_GB   
Ign http://ppa.launchpad.net oneiric/main Translation-en_GB          
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Ign http://archive.canonical.com oneiric/partner Translation-en      
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://ppa.launchpad.net oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Get:1 http://archive.ubuntu.com oneiric/main Translation-en_GB [69.0 kB]
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Get:2 http://archive.ubuntu.com oneiric/multiverse Translation-en_GB [68.5 kB] 
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Get:3 http://archive.ubuntu.com oneiric/restricted Translation-en_GB [1,937 B] 
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Get:4 http://archive.ubuntu.com oneiric/universe Translation-en_GB [4,365 B]   
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Fetched 144 kB in 11s (12.2 kB/s)                                              
Reading package lists... Done
alessandro@Alessandro:~$ 

```


hi man 

   Yup! its looking good .Now you can go for  
```
sudo apt-get upgrade
```

Enjoy The Ubuntu

---

### Post by IL TRIVELLA on 2011-10-25
> **raja.genupula said:**
> hi man 

   Yup! its looking good .Now you can go for  
```
sudo apt-get upgrade
```Enjoy The Ubuntu

I did it... 

```
alessandro@Alessandro:~$ sudo apt-get upgrade
[sudo] password for alessandro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
alessandro@Alessandro:~$ 
```

it's okay? for what is this upgrade???

---

### Post by raja.genupula on 2011-10-25
Hi man 
       I suggested you this , if your system have any new updates to install then its gonna show them.to check updates and to install them i trust only terminal way.
and i used to do as 

```
sudo apt-get update
sudo apt-get upgrade
```

enjoy the Ubuntu

---

### Post by IL TRIVELLA on 2011-10-25
> **raja.genupula said:**
> Hi man 
       I suggested you this , if your system have any new updates to install then its gonna show them.to check updates and to install them i trust only terminal way.
and i used to do as 

```
sudo apt-get update
sudo apt-get upgrade
```enjoy the Ubuntu

ok thanks, but I still don't understand for what is the upgrade...

---

### Post by raja.genupula on 2011-10-25
> **IL TRIVELLA said:**
> ok thanks, but I still don't understand for what is the upgrade...

if your system having any security upgrade or fixes & application updates all you can get by doing upgrade of your system.

i mean with this

sudo apt-get upgrade

---

### Post by IL TRIVELLA on 2011-10-30
> **raja.genupula said:**
> if your system having any security upgrade or fixes & application updates all you can get by doing upgrade of your system.

i mean with this

sudo apt-get upgrade

thanks, for all your support and help, and of course patience, really kind =)

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

---

