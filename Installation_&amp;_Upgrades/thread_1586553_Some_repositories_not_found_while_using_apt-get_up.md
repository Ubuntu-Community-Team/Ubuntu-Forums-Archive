---
title: "Some repositories not found while using apt-get update"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by durga11 on 2010-10-02
I am new to ubuntu.I am using ubuntu 9.10. while updating through command line It is unable to fetch some of the repositories.  I am facing the same problem as "repository indexes could not be downloaded" while running from update-manager.

durga@durga-laptop:~$ sudo apt-get update 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic Release.gpg
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/universe Translation-en_IN           
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/multiverse Translation-en_IN         
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/main Translation-en_IN               
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/restricted Translation-en_IN         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates Release.gpg                  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_IN                
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/universe Translation-en_IN   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN                     
Ign [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/multiverse Translation-en_IN 
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic Release                              
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates Release                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_IN            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]                    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/universe Packages                    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/universe Sources                     
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/multiverse Sources                   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/multiverse Packages                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/main Packages                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/restricted Packages                  
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/main Sources                         
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic/restricted Sources                   
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/universe Packages            
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg [307B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_IN                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/universe Sources             
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/multiverse Sources           
Hit [http://ubuntuarchive.hnsdc.com](http://ubuntuarchive.hnsdc.com) karmic-updates/multiverse Packages          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release [66.0kB]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                                                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN                                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN                                                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                                                                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                                                                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                                                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                                                                                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages                                                                                                       
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                                                                                           
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.167 80]
Fetched 9,742B in 13s (697B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: Failed to fetch [http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.167 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


 I am using a wireless internet and  didnt configure the network proxy as I can access the internet.

Please find the attached soures.list file  and let me know ifany packages needs to be removed.

---

