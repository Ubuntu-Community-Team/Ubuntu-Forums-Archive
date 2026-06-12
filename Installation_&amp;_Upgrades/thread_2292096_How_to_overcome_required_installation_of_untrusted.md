---
title: "How to overcome required installation of untrusted packages?"
date: 2015-08-25
forum: Installation &amp; Upgrades
---

### Post by tomerbd on 2015-08-25
How to overcome:

```
$ sudo apt-get update
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty InRelease
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://eric.lavar.de](http://eric.lavar.de) experimental/ InRelease                               
Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Ign [http://dl.bintray.com](http://dl.bintray.com)  InRelease                                           
Get:2 [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease [1,952 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Get:3 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Get:4 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:6 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty Release [58.5 kB]                    
Get:7 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates Release [63.5 kB]            
Get:8 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:9 [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages [561 B]           
Get:10 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports Release [63.5 kB]         
Ign [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ InRelease                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:11 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                           
Get:12 [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages [561 B]           
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:14 [http://dl.bintray.com](http://dl.bintray.com)  Release.gpg [821 B]                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:15 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,195 B]               
Get:16 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]                     
Get:17 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/main Sources [1,064 kB]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:18 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages [14 B]              
Get:19 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,204 B]                
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:21 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/restricted Sources [5,433 B]        
Get:22 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]               
Get:23 [http://dl.bintray.com](http://dl.bintray.com)  Release [487 B]                                  
Ign [http://dl.bintray.com](http://dl.bintray.com)  Release                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:24 [http://eric.lavar.de](http://eric.lavar.de) experimental/ Release.gpg [198 B]                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Get:26 [http://dl.bintray.com](http://dl.bintray.com)  Packages [1,026 B]                               
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Get:28 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Get:29 [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Release.gpg [198 B]                        
Get:30 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_US                  
Get:31 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en                     
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [63.5 kB]            
Get:33 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Get:34 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg [316 B]                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:35 [https://get.docker.com](https://get.docker.com) docker InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Get:36 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                       
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [92.2 kB]       
Get:38 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Ign [http://dl.bintray.com](http://dl.bintray.com)  Translation-en_US                                   
Get:39 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B] 
Get:40 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                       
Get:41 [http://eric.lavar.de](http://eric.lavar.de) experimental/ Release [1,147 B]                    
Ign [http://eric.lavar.de](http://eric.lavar.de) experimental/ Release                                 
Ign [https://get.docker.com](https://get.docker.com) docker InRelease                                    
Get:42 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Ign [http://dl.bintray.com](http://dl.bintray.com)  Translation-en                                      
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [29.8 kB]   
Get:44 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.5 kB]                       
Get:45 [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Release [1,129 B]                          
Ign [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Release                                       
Get:46 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [14.0 kB]                       
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2,330 B] 
Get:48 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release [15.1 kB]                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:49 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/universe Sources [6,399 kB]         
Get:50 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [1,126 B]           
Get:51 [https://get.docker.com](https://get.docker.com) docker Release                                   
Get:52 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [1,126 B]            
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [333 kB] 
Get:54 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/multiverse Sources [174 kB]         
Get:55 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [854 B]             
Get:56 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8,875 B]
Get:57 [https://get.docker.com](https://get.docker.com) docker/main amd64 Packages                       
Get:58 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [854 B]              
Get:59 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/main amd64 Packages [1,350 kB]      
Get:60 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [566 B]             
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [114 kB]
Get:62 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/restricted amd64 Packages [13.0 kB] 
Get:63 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [563 B]             
Get:64 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [570 B]              
Get:65 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,686 B]
Get:66 [https://get.docker.com](https://get.docker.com) docker/main i386 Packages                        
Get:67 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [583 B]             
Get:68 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [583 B]              
Get:69 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [317 kB]  
Get:70 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [413 B]             
Get:71 [https://get.docker.com](https://get.docker.com) docker/main Translation-en_US                    
Get:72 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [1,719 B]           
Get:73 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,846 B]
Get:74 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [1,734 B]            
Get:75 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [741 B]             
Get:76 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [114 kB]
Get:77 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [707 B]             
Get:78 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [707 B]              
Get:79 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,830 B]
Get:80 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [519 B]             
Get:81 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en [181 kB] 
Get:82 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [519 B]              
Get:83 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [245 B]             
Get:84 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en [1,679 B]
Get:85 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en [2,266 B]
Get:86 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en [66.9 kB]
Get:87 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/universe amd64 Packages [5,859 kB]  
Get:88 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/multiverse amd64 Packages [132 kB]  
Get:89 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/main i386 Packages [1,348 kB]       
Get:90 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/restricted i386 Packages [13.4 kB]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
  404  Not Found
Get:91 [http://eric.lavar.de](http://eric.lavar.de) experimental/ Packages [2,266 B]                   
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                 
Get:92 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/universe i386 Packages [5,866 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:93 [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Packages [2,048 B]                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:94 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/multiverse i386 Packages [134 kB]   
Get:95 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/main Translation-en [762 kB]        
Ign [http://eric.lavar.de](http://eric.lavar.de) experimental/ Translation-en_US                       
Get:96 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/multiverse Translation-en [102 kB]  
Get:97 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/restricted Translation-en [3,457 B] 
Ign [http://eric.lavar.de](http://eric.lavar.de) experimental/ Translation-en                          
Ign [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Translation-en_US                             
Ign [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Translation-en                                
Get:98 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/universe Translation-en [4,089 kB]  
Get:99 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/main Sources [230 kB]       
Get:100 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/restricted Sources [4,725 B]
Get:101 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/universe Sources [134 kB]  
Get:102 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/multiverse Sources [5,143 B]
Get:103 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/main amd64 Packages [606 kB]
Get:104 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15.4 kB]
Get:105 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/universe amd64 Packages [309 kB]
Get:106 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:107 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/main i386 Packages [586 kB]
Get:108 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15.1 kB]
Ign [https://get.docker.com](https://get.docker.com) docker/main Translation-en_US                       
Get:109 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/universe i386 Packages [310 kB]
Get:110 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [12.1 kB]
Get:111 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/main Translation-en [292 kB]
Get:112 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6,148 B]
Get:113 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/restricted Translation-en [3,560 B]
Get:114 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-updates/universe Translation-en [164 kB]
Get:115 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/main Sources [5,860 B]   
Get:116 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/restricted Sources [28 B]
Get:117 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/universe Sources [28.4 kB]
Get:118 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/multiverse Sources [1,898 B]
Get:119 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/main amd64 Packages [6,288 B]
Get:120 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Get:121 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/universe amd64 Packages [32.6 kB]
Get:122 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1,571 B]
Get:123 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/main i386 Packages [6,293 B]
Get:124 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Get:125 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/universe i386 Packages [32.6 kB]
Get:126 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1,552 B]
Get:127 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/main Translation-en [3,645 B]
Get:128 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/multiverse Translation-en [1,215 B]
Get:129 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Get:130 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty-backports/universe Translation-en [29.6 kB]
Ign [https://get.docker.com](https://get.docker.com) docker/main Translation-en                          
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) trusty/universe Translation-en_US             
Fetched 31.9 MB in 13s (2,351 kB/s)                                            
W: GPG error: [http://dl.bintray.com](http://dl.bintray.com)  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 99E82A75642AC823
W: GPG error: [http://eric.lavar.de](http://eric.lavar.de) experimental/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 27CD3F36869D2871
W: GPG error: [http://eric.lavar.de](http://eric.lavar.de) ubuntu/ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 27CD3F36869D2871
W: Failed to fetch [http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by v3.xx on 2015-08-25
GPG error can be solved in a few ways.  Take your choice ..

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)

That 404 error is because there is no Trusty package ..

[http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/](http://ppa.launchpad.net/disper-dev/ppa/ubuntu/dists/)

So you need to remove that ppa with software sources.  Open a terminal and pull it up.

```
software-properties-gtk
```

---

### Post by tomerbd on 2015-08-25
thanks I used according to url you sent

> $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 99E82A75642AC823 27CD3F36869D2871

and fixed

---

