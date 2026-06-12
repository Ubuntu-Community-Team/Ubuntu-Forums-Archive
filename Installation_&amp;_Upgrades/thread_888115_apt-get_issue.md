---
title: "apt-get issue"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by banditti on 2008-08-12
Has anyone seen this or have thoughts?  It has been doing it for a couple of days.   Tried a quick search with not much.

```
 apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Hit http://security.ubuntu.com hardy-security Release.gpg                                          
Ign http://apt.wicd.net hardy Release.gpg                                                          
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                                     
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                                   
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US                                 
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US    
  Error reading from server - read (104 Connection reset by peer)
Ign http://apt.wicd.net hardy/extras Translation-en_US                        
Get:1 http://us.archive.ubuntu.com hardy-updates Release.gpg [189B]  
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                            
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US                               
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US                          
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US                           
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US 
Hit http://security.ubuntu.com hardy-security Release                       
Ign http://us.archive.ubuntu.com hardy Release                              
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://security.ubuntu.com hardy-security/main Packages                                                            
Hit http://security.ubuntu.com hardy-security/restricted Packages                                                      
Get:2 http://apt.wicd.net hardy Release [29.1kB]                                                  
Hit http://security.ubuntu.com hardy-security/main Sources                                        
Hit http://security.ubuntu.com hardy-security/restricted Sources                                  
Hit http://security.ubuntu.com hardy-security/universe Packages                                   
Hit http://security.ubuntu.com hardy-security/universe Sources                                    
Hit http://security.ubuntu.com hardy-security/multiverse Packages                                 
Hit http://security.ubuntu.com hardy-security/multiverse Sources                                  
Hit http://apt.wicd.net hardy/extras Packages                                                     
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources     
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources 
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Fetched 190B in 1s (127B/s)                             
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.46 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by tuxxy on 2008-08-12
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/235246](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/235246)

---

### Post by Mhurst1 on 2008-08-12
Nope works fine for me

---

