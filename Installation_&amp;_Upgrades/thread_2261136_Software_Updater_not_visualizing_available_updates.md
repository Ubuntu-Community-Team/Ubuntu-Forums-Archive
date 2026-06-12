---
title: "Software Updater not visualizing available updates -failed to connect to the internet"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by gianfranco2 on 2015-01-16
I've had this problem for a while, and, more than anything else, it's just a little annoyance because whenever I launch the updater, it says *Failed to download repository information, check your Internet connection;* *BUT* when I press the settings button and then click on close, the available updates are shown. This is what I see when I run the *sudo apt-get update *command:
```
Ign http://liveusb.info all InRelease                                          
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://deb.opera.com stable InRelease                                      
Hit http://liveusb.info all Release.gpg                                        
Get:1 http://archive.canonical.com trusty Release.gpg [933 B]                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://liveusb.info all Release                                            
Hit http://archive.canonical.com trusty Release                                
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://www.xylasoft.com precise InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://liveusb.info all/main amd64 Packages                                
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://archive.ubuntu.com trusty-updates InRelease                         
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://liveusb.info all/main i386 Packages                                 
Hit http://www.xylasoft.com precise/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://archive.getdeb.net trusty-getdeb InRelease                          
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://www.xylasoft.com precise/main i386 Packages                         
Ign http://archive.ubuntu.com trusty-backports InRelease                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.getdeb.net trusty-getdeb/apps amd64 Packages                
Ign http://archive.ubuntu.com trusty-security InRelease                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:2 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.getdeb.net trusty-getdeb/apps i386 Packages                 
Hit http://archive.ubuntu.com trusty-backports Release.gpg                     
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:3 http://archive.ubuntu.com trusty-security Release.gpg [933 B]            
Hit http://archive.ubuntu.com trusty Release                                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:4 http://archive.ubuntu.com trusty-updates Release [62,0 kB]               
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty-backports Release                         
Get:5 http://archive.ubuntu.com trusty-security Release [62,0 kB]              
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Ign http://liveusb.info all/main Translation-en_US                             
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://liveusb.info all/main Translation-en                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://deb.opera.com stable/non-free Translation-en                        
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://www.xylasoft.com precise/main Translation-en_US                     
Hit http://archive.ubuntu.com trusty/main i386 Packages            
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://www.xylasoft.com precise/main Translation-en                        
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Get:6 http://archive.ubuntu.com trusty-updates/main Sources [155 kB]           
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:7 http://archive.ubuntu.com trusty-updates/restricted Sources [2.061 B]    
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:8 http://archive.ubuntu.com trusty-updates/universe Sources [97,6 kB]      
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:9 http://archive.ubuntu.com trusty-updates/multiverse Sources [3.550 B]    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:10 http://archive.ubuntu.com trusty-updates/main amd64 Packages [398 kB]   
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:11 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [8.875 B]
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:12 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [239 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:13 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9.373 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:14 http://archive.ubuntu.com trusty-updates/main i386 Packages [390 kB]    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:15 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [8.846 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:16 http://archive.ubuntu.com trusty-updates/universe i386 Packages [240 kB]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:17 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [9.567 B]
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/main Translation-en               
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en           
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/main Sources                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/restricted Sources              
Hit http://archive.ubuntu.com trusty-backports/universe Sources                
Ign http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages         
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages              
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages          
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Hit http://ppa.launchpad.net trusty Release                                    
Get:18 http://archive.ubuntu.com trusty-security/main Sources [63,1 kB]        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:19 http://archive.ubuntu.com trusty-security/restricted Sources [2.061 B]  
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:20 http://archive.ubuntu.com trusty-security/universe Sources [17,4 kB]    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:21 http://archive.ubuntu.com trusty-security/multiverse Sources [716 B]    
Get:22 http://archive.ubuntu.com trusty-security/main amd64 Packages [196 kB]  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Get:23 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [8.875 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:24 http://archive.ubuntu.com trusty-security/universe amd64 Packages [84,2 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:25 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [1.166 B]
Get:26 http://archive.ubuntu.com trusty-security/main i386 Packages [187 kB]   
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:27 http://archive.ubuntu.com trusty-security/restricted i386 Packages [8.846 B]
Get:28 http://archive.ubuntu.com trusty-security/universe i386 Packages [84,2 kB]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:29 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [1.412 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
Fetched 2.344 kB in 1min 33s (25,1 kB/s)
W: Failed to fetch http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/hydr0g3n/qbittorrent-stable/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

```
I'm not sure what to do in this situation. Fair enough, I know the problem is trivial and it looks like I have found a workaround already, but is there a way to solve this?

---

### Post by gianfranco2 on 2015-01-16
I have removed the qBitTorrent repository, and now I am getting the following error:
```
Err [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages
  504  Gateway Time-out [IP: 91.189.92.191 80]
Err [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages
  504  Gateway Time-out [IP: 91.189.92.191 80]
Fetched 2.002 kB in 4min 12s (7.913 B/s)
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages](http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-amd64/Packages)  504  Gateway Time-out [IP: 91.189.92.191 80]


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/trusty/partner/binary-i386/Packages)  504  Gateway Time-out [IP: 91.189.92.191 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```
However, Software Updater seems to be working properly now.

---

