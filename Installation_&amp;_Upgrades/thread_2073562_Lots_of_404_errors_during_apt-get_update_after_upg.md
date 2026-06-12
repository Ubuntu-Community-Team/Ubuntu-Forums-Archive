---
title: "Lots of 404 errors during apt-get update after upgrading to 12.10"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by Stonecold1995 on 2012-10-19
```
alex@kubuntu:~$ sudo apt-get update
Ign http://extras.ubuntu.com quantal InRelease
Ign http://archive.canonical.com quantal InRelease                                                                                       
Ign http://ppa.launchpad.net quantal InRelease                                                                                           
Ign http://archive.ubuntu.com quantal InRelease                                                                                          
Hit http://extras.ubuntu.com quantal Release.gpg                                                                                         F
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.canonical.com quantal Release.gpg                                                                                      
Ign http://archive.ubuntu.com quantal-updates InRelease                                                                                   
Hit http://extras.ubuntu.com quantal Release                                                                                              
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                   
Hit http://archive.canonical.com quantal Release                                                                                          
Ign http://archive.ubuntu.com quantal-backports InRelease                                                                                                        
Hit http://extras.ubuntu.com quantal/main Sources                                                                                         
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.canonical.com quantal/partner Sources                                                                                  
Ign http://archive.ubuntu.com quantal-security InRelease                                                                                  
Hit http://extras.ubuntu.com quantal/main amd64 Packages                                                                                  
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.canonical.com quantal/partner amd64 Packages                                                                           
Ign http://archive.ubuntu.com quantal-proposed InRelease                                                                                  
Hit http://extras.ubuntu.com quantal/main i386 Packages                                                                                   
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.canonical.com quantal/partner i386 Packages                                                                            
Hit http://archive.ubuntu.com quantal Release.gpg                                                                                         
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal-updates Release.gpg                                                                                 
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal-backports Release.gpg                                                                               
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal-security Release.gpg                                                                                
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal-proposed Release.gpg                                                                                
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal Release                                                                                             
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                                         
Hit http://archive.ubuntu.com quantal-updates Release                                                                                                           
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                                         
Hit http://archive.ubuntu.com quantal-backports Release                                                                                                         
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                                         
Hit http://archive.ubuntu.com quantal-security Release                                                                                                          
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                                                                                                            
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                  
Hit http://archive.ubuntu.com quantal-proposed Release                                                                                    
Ign http://archive.canonical.com quantal/partner Translation-en_US                                                                                                                     
Ign http://extras.ubuntu.com quantal/main Translation-en                                                                                                        
Ign http://ppa.launchpad.net quantal InRelease                                                                                            
Hit http://archive.ubuntu.com quantal/restricted Sources                                                                                  
Ign http://archive.canonical.com quantal/partner Translation-en                                                     
Hit http://ppa.launchpad.net quantal Release.gpg                                                                    
Hit http://archive.ubuntu.com quantal/main Sources                                                                  
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://ppa.launchpad.net quantal Release.gpg                                                                    
Hit http://archive.ubuntu.com quantal/multiverse Sources                                                            
Hit http://archive.ubuntu.com quantal/universe Sources                                        
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/main amd64 Packages                                     
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/restricted amd64 Packages                               
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/universe amd64 Packages                                 
Ign http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/multiverse amd64 Packages                               
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/main i386 Packages                                      
Ign http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/restricted i386 Packages                                
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/universe i386 Packages                                  
Ign http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/multiverse i386 Packages                                
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Ign http://dl.google.com stable InRelease                                                     
Ign http://ppa.launchpad.net quantal Release.gpg                                                      
Hit http://dl.google.com stable Release.gpg                                                           
Hit http://archive.ubuntu.com quantal/main Translation-en                                             
Hit http://dl.google.com stable Release                                                               
Hit http://dl.google.com stable/main amd64 Packages                                         
Hit http://dl.google.com stable/main i386 Packages                   
Hit http://ppa.launchpad.net quantal Release.gpg                     
Hit http://packages.medibuntu.org quantal InRelease                  
Hit http://ppa.launchpad.net quantal Release.gpg                                              
Hit http://archive.ubuntu.com quantal/multiverse Translation-en                                       
Ign http://ppa.launchpad.net quantal Release.gpg                                                      
Hit http://packages.medibuntu.org quantal/free amd64 Packages                                         
Ign http://dl.google.com stable/main Translation-en_US               
Hit http://ppa.launchpad.net quantal Release                                                          
Ign http://dl.google.com stable/main Translation-en                                                                                                
Hit http://archive.ubuntu.com quantal/restricted Translation-en                                                             
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://packages.medibuntu.org quantal/non-free amd64 Packages                           
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal/universe Translation-en                                                                
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://packages.medibuntu.org quantal/free i386 Packages                                
Hit http://archive.ubuntu.com quantal-updates/restricted Sources                                      
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/main Sources                                  
Hit http://packages.medibuntu.org quantal/non-free i386 Packages     
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/multiverse Sources                                                             
Ign http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/universe Sources                  
Hit http://ppa.launchpad.net quantal Release   
Hit http://archive.ubuntu.com quantal-updates/main amd64 Packages                                                            
Ign http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/restricted amd64 Packages         
Hit http://ppa.launchpad.net quantal Release   
Hit http://archive.ubuntu.com quantal-updates/universe amd64 Packages                                                        
Ign http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/multiverse amd64 Packages         
Hit http://ppa.launchpad.net quantal Release   
Hit http://archive.ubuntu.com quantal-updates/main i386 Packages                                                             
Ign http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/restricted i386 Packages          
Hit http://ppa.launchpad.net quantal Release   
Hit http://archive.ubuntu.com quantal-updates/universe i386 Packages                                                         
Hit http://ppa.launchpad.net quantal Release                                                          
Hit http://archive.ubuntu.com quantal-updates/multiverse i386 Packages                      
Ign http://ppa.launchpad.net quantal Release                         
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-updates/main Translation-en               
Hit http://ppa.launchpad.net quantal/main amd64 Packages                        
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com quantal-updates/restricted Translation-en         
Hit http://ppa.launchpad.net quantal/main Sources                    
Hit http://archive.ubuntu.com quantal-updates/universe Translation-en           
Hit http://ppa.launchpad.net quantal/main amd64 Packages                        
Hit http://archive.ubuntu.com quantal-backports/main Sources         
Hit http://ppa.launchpad.net quantal/main i386 Packages                         
Hit http://archive.ubuntu.com quantal-backports/restricted Sources              
Hit http://archive.ubuntu.com quantal-backports/universe Sources                
Hit http://archive.ubuntu.com quantal-backports/multiverse Sources              
Hit http://ppa.launchpad.net quantal/main Sources                               
Hit http://archive.ubuntu.com quantal-backports/main amd64 Packages
Hit http://ppa.launchpad.net quantal/main amd64 Packages                                              
Hit http://archive.ubuntu.com quantal-backports/restricted amd64 Packages                             
Hit http://ppa.launchpad.net quantal/main i386 Packages                         
Hit http://archive.ubuntu.com quantal-backports/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/multiverse amd64 Packages       
Hit http://archive.ubuntu.com quantal-backports/main i386 Packages              
Hit http://ppa.launchpad.net quantal/main Sources                               
Hit http://archive.ubuntu.com quantal-backports/restricted i386 Packages        
Hit http://ppa.launchpad.net quantal/main amd64 Packages                        
Hit http://archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages              
Hit http://archive.ubuntu.com quantal-backports/multiverse i386 Packages                              
Hit http://ppa.launchpad.net quantal/main Sources                                                     
Hit http://archive.ubuntu.com quantal-backports/main Translation-en             
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal-backports/multiverse Translation-en       
Ign http://packages.medibuntu.org quantal/free Translation-en_US                
Hit http://ppa.launchpad.net quantal/main i386 Packages                                               
Hit http://archive.ubuntu.com quantal-backports/restricted Translation-en                             
Ign http://packages.medibuntu.org quantal/free Translation-en                   
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-backports/universe Translation-en
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Ign http://packages.medibuntu.org quantal/non-free Translation-en_US
Hit http://archive.ubuntu.com quantal-security/restricted Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages                         
Hit http://archive.ubuntu.com quantal-security/main Sources                     
Ign http://packages.medibuntu.org quantal/non-free Translation-en               
Hit http://archive.ubuntu.com quantal-security/multiverse Sources
Hit http://archive.ubuntu.com quantal-security/universe Sources
Hit http://archive.ubuntu.com quantal-security/main amd64 Packages
Hit http://archive.ubuntu.com quantal-security/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-security/universe amd64 Packages
Hit http://archive.ubuntu.com quantal-security/multiverse amd64 Packages
Hit http://archive.ubuntu.com quantal-security/main i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal-security/restricted i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-security/universe i386 Packages
Hit http://archive.ubuntu.com quantal-security/multiverse i386 Packages
Hit http://archive.ubuntu.com quantal-security/main Translation-en
Hit http://archive.ubuntu.com quantal-security/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-security/restricted Translation-en
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-security/universe Translation-en
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal-proposed/restricted Sources
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-proposed/main Sources
Hit http://archive.ubuntu.com quantal-proposed/multiverse Sources
Hit http://archive.ubuntu.com quantal-proposed/universe Sources
Hit http://archive.ubuntu.com quantal-proposed/restricted amd64 Packages
Hit http://archive.ubuntu.com quantal-proposed/main amd64 Packages
Hit http://archive.ubuntu.com quantal-proposed/multiverse amd64 Packages    
Hit http://archive.ubuntu.com quantal-proposed/universe amd64 Packages      
Hit http://archive.ubuntu.com quantal-proposed/restricted i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-proposed/main i386 Packages
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://archive.ubuntu.com quantal-proposed/multiverse i386 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://archive.ubuntu.com quantal-proposed/universe i386 Packages
Hit http://archive.ubuntu.com quantal-proposed/main Translation-en
Hit http://archive.ubuntu.com quantal-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com quantal-proposed/restricted Translation-en
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://archive.ubuntu.com quantal-proposed/universe Translation-en
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Hit http://ppa.launchpad.net quantal/main Sources
Hit http://ppa.launchpad.net quantal/main amd64 Packages
Hit http://ppa.launchpad.net quantal/main i386 Packages
Ign http://archive.ubuntu.com quantal/main Translation-en_US
Ign http://archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-security/main Translation-en_US
Ign http://archive.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-security/universe Translation-en_US
Ign http://archive.ubuntu.com quantal-proposed/main Translation-en_US
Ign http://archive.ubuntu.com quantal-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com quantal-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com quantal-proposed/universe Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Err http://ppa.launchpad.net quantal/main Sources
  404  Not Found
Err http://ppa.launchpad.net quantal/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net quantal/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/rvm/mplayer/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/zveroy/aegisub/ubuntu/dists/quantal/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/zveroy/aegisub/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/zveroy/aegisub/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Where can I find the PPAs that work for 12.10?

---

### Post by drmrgd on 2012-10-19
Most of those look like third party PPAs from Launch Pad (boy you sure have a lot of them!).  I'll bet, since Quantal was just released, that they don't have a repo setup for Quantal yet.  You may have to wait until they update their repositories in order to get packages from them.

---

### Post by Stonecold1995 on 2012-10-30
Is there any way to remove the duplicates of things like "Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US"?  It seems that near the end this repeats several times.

---

### Post by drmrgd on 2012-10-30
Yeah, I noticed that too.  Have a look at your software sources list with either the Software Updater or in the terminal (/etc/apt/sources.list or /etc/apt/sources.list.d), and look for duplicate entries.  You can just delete the entries you don't need.  Make a backup copy of /etc/apt/sources.list first just in case you mess it up.

---

### Post by Stonecold1995 on 2012-10-31
I couldn't find any duplicate entries with Synaptic Package Manager, /etc/apt/sources.list, or /etc/apt/sources.list.d/.

---

