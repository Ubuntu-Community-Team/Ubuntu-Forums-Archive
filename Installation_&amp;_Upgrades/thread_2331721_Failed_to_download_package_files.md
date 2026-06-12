---
title: "Failed to download package files"
date: 2016-07-25
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2016-07-25
I get this message when I try to do an update with Software Updater. There is nothing wrong with my internet connection.

Attached is the list I get when I "sudo apt-get update"
```
john@john-OptiPlex-755:~$ sudo apt-get update
[sudo] password for john: 
Ign http://dl.google.com stable InRelease
Hit http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://au.archive.ubuntu.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:1 http://repository.spotify.com stable InRelease [3,302 B]                 
Err http://repository.spotify.com stable InRelease                             
  
Hit http://dl.google.com stable Release.gpg                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:2 http://au.archive.ubuntu.com trusty-updates InRelease [65.9 kB]          
Hit http://security.ubuntu.com trusty-security/main Sources                    
Get:3 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://dl.google.com stable Release                                        
Hit http://archive.canonical.com trusty Release                                
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://security.ubuntu.com trusty-security/universe Sources                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://security.ubuntu.com trusty-security/multiverse Sources              
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://au.archive.ubuntu.com trusty-backports InRelease                    
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://security.ubuntu.com trusty-security/restricted Sources              
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:4 https://tiliado.eu trusty InRelease                                      
Err https://tiliado.eu trusty InRelease                                        
  
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://au.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:5 http://au.archive.ubuntu.com trusty-updates/main Sources [279 kB]        
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/multiverse i386 Packages        
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Ign http://ppa.launchpad.net trusty Release                                    
Ign http://extras.ubuntu.com trusty/main Translation-en_AU                   
Hit http://ppa.launchpad.net trusty Release             
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex              
Get:6 http://au.archive.ubuntu.com trusty-updates/universe Sources [158 kB]    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:7 http://au.archive.ubuntu.com trusty-updates/multiverse Sources [5,929 B] 
Get:8 http://au.archive.ubuntu.com trusty-updates/restricted Sources [5,352 B] 
Get:9 http://au.archive.ubuntu.com trusty-updates/main i386 Packages [765 kB]  
Ign http://ppa.launchpad.net trusty/main Translation-en_AU                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Get:10 http://au.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:11 http://au.archive.ubuntu.com trusty-updates/universe i386 Packages [365 kB]
Get:12 http://au.archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.6 kB]
Hit http://au.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://au.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://au.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://au.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://au.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://au.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://au.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://au.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://au.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://au.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://au.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://au.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://au.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://au.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://au.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://au.archive.ubuntu.com trusty-backports/universe Translation-en      
Hit http://au.archive.ubuntu.com trusty Release                                
Hit http://au.archive.ubuntu.com trusty/main Sources                           
Hit http://au.archive.ubuntu.com trusty/universe Sources                       
Hit http://au.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://au.archive.ubuntu.com trusty/restricted Sources                     
Hit http://au.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://au.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://au.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://au.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://au.archive.ubuntu.com trusty/main Translation-en_AU                 
Hit http://au.archive.ubuntu.com trusty/main Translation-en                    
Hit http://au.archive.ubuntu.com trusty/multiverse Translation-en_AU           
Hit http://au.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://au.archive.ubuntu.com trusty/restricted Translation-en_AU           
Hit http://au.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://au.archive.ubuntu.com trusty/universe Translation-en_AU             
Hit http://au.archive.ubuntu.com trusty/universe Translation-en                
Fetched 1,692 kB in 35s (47.9 kB/s)                                            
Reading package lists... Done
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 13B00F1FD2C19886

W: There is no public key available for the following key IDs:
1397BC53640DB551
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://tiliado.eu trusty InRelease: The following signatures were invalid: KEYEXPIRED 1435053600 KEYEXPIRED 1435053600 KEYEXPIRED 1435053600

W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  

W: Failed to fetch https://tiliado.eu/nuvolaplayer/repository/deb/dists/trusty/InRelease  

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://ppa.launchpad.net/nuvola-player-builders/stable/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
john@john-OptiPlex-755:~$ ^C
john@john-OptiPlex-755:~$ 

```

Any hints?

---

### Post by JohnMac on 2016-08-24
I was disappointed that I had no replies to my post. I have since upgraded to Ubuntu 16.04, the upgrade went well.

---

### Post by howefield on 2016-08-24
To be honest, a daily bump is usually more productive than a monthly whine ;)

Glad to hear that you are up and running.

---

