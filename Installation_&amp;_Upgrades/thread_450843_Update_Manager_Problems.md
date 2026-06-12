---
title: "Update Manager Problems"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by masterperas on 2007-05-21
im running a ubuntu box wich i upgraded to feisty a week ago.

All of a sudden i started getting the "fix broken packages" dialog whenever i try to update my system thru the update manager. i tried fixing it through synaptic but it didnt work. dont know what to do now

this is what i get when i run apt-get -f update :
```
sapiens@peraspor:~$ sudo apt-get -f update
Get:1 http://pt.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://pt.archive.ubuntu.com feisty/main Translation-en_US                 
Ign http://pt.archive.ubuntu.com feisty/restricted Translation-en_US           
Get:2 http://pt.archive.ubuntu.com feisty-updates Release.gpg [191B]           
Ign http://pt.archive.ubuntu.com feisty-updates/main Translation-en_US         
Ign http://pt.archive.ubuntu.com feisty-updates/restricted Translation-en_US   
Get:3 http://archive.ubuntu.com feisty-backports Release.gpg [191B]            
Ign http://archive.ubuntu.com feisty-backports/main Translation-en_US          
Hit http://pt.archive.ubuntu.com feisty Release                                
Hit http://pt.archive.ubuntu.com feisty-updates Release                        
Ign http://archive.ubuntu.com feisty-backports/restricted Translation-en_US    
Ign http://archive.ubuntu.com feisty-backports/universe Translation-en_US      
Ign http://archive.ubuntu.com feisty-backports/multiverse Translation-en_US    
Get:4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]              
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US        
Ign http://archive.ubuntu.com feisty-updates/multiverse Translation-en_US      
Get:5 http://security.ubuntu.com feisty-security Release.gpg [191B]            
Ign http://security.ubuntu.com feisty-security/main Translation-en_US          
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US    
Get:6 http://archive.ubuntu.com feisty-security Release.gpg [191B]             
Ign http://archive.ubuntu.com feisty-security/main Translation-en_US           
Ign http://archive.ubuntu.com feisty-security/restricted Translation-en_US     
Ign http://archive.ubuntu.com feisty-security/universe Translation-en_US       
Ign http://archive.ubuntu.com feisty-security/multiverse Translation-en_US     
Get:7 http://archive.canonical.com feisty-commercial Release.gpg [191B]        
Ign http://archive.canonical.com feisty-commercial/main Translation-en_US      
Get:8 http://archive.ubuntu.com feisty Release.gpg [191B]                      
Ign http://archive.ubuntu.com feisty/universe Translation-en_US                
Hit http://security.ubuntu.com feisty-security Release                         
Ign http://archive.ubuntu.com feisty/multiverse Translation-en_US              
Hit http://archive.ubuntu.com feisty-backports Release                         
Hit http://archive.ubuntu.com feisty-updates Release                           
Hit http://archive.canonical.com feisty-commercial Release                     
Hit http://pt.archive.ubuntu.com feisty/main Packages                          
Hit http://archive.ubuntu.com feisty-security Release                          
Hit http://archive.ubuntu.com feisty Release                                   
Hit http://security.ubuntu.com feisty-security/main Packages                   
Hit http://pt.archive.ubuntu.com feisty/restricted Packages                    
Hit http://pt.archive.ubuntu.com feisty/main Sources                           
Hit http://pt.archive.ubuntu.com feisty/restricted Sources                     
Hit http://pt.archive.ubuntu.com feisty-updates/main Packages                  
Hit http://pt.archive.ubuntu.com feisty-updates/restricted Packages            
Hit http://pt.archive.ubuntu.com feisty-updates/main Sources                   
Hit http://pt.archive.ubuntu.com feisty-updates/restricted Sources             
Hit http://archive.canonical.com feisty-commercial/main Packages               
Hit http://security.ubuntu.com feisty-security/restricted Packages             
Hit http://security.ubuntu.com feisty-security/main Sources                    
Hit http://archive.ubuntu.com feisty-backports/main Packages                   
Hit http://security.ubuntu.com feisty-security/restricted Sources              
Hit http://archive.ubuntu.com feisty-backports/restricted Packages            
Hit http://archive.ubuntu.com feisty-backports/universe Packages              
Hit http://archive.ubuntu.com feisty-backports/multiverse Packages            
Hit http://archive.ubuntu.com feisty-updates/universe Packages                
Hit http://archive.ubuntu.com feisty-updates/multiverse Packages              
Hit http://archive.ubuntu.com feisty-security/main Packages                   
Hit http://archive.ubuntu.com feisty-security/restricted Packages             
Hit http://archive.ubuntu.com feisty-security/universe Packages               
Hit http://archive.ubuntu.com feisty-security/multiverse Packages             
Hit http://archive.ubuntu.com feisty/universe Packages                        
Hit http://archive.ubuntu.com feisty/multiverse Packages                      
Get:9 http://medibuntu.sos-sts.com feisty Release.gpg [189B]                  
Ign http://medibuntu.sos-sts.com feisty/free Translation-en_US
Ign http://medibuntu.sos-sts.com feisty/non-free Translation-en_US
Hit http://medibuntu.sos-sts.com feisty Release
Err http://medibuntu.sos-sts.com feisty Release
  
Get:10 http://medibuntu.sos-sts.com feisty Release [7232B]
Ign http://medibuntu.sos-sts.com feisty Release                                
Hit http://medibuntu.sos-sts.com feisty/free Packages                          
Hit http://medibuntu.sos-sts.com feisty/non-free Packages                      
Hit http://medibuntu.sos-sts.com feisty/free Sources                           
Hit http://medibuntu.sos-sts.com feisty/non-free Sources                       
Fetched 7429B in 7s (942B/s)                                                   
Reading package lists... Done
W: GPG error: http://medibuntu.sos-sts.com feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by taurus on 2007-05-21
Try

```
wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by masterperas on 2007-05-27
i managed to update everything but the "hal" package its stuck in there in the update manager

---

