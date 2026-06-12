---
title: "eeebuntu can't update or upgrade"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by arnicainthemembrane on 2014-12-31
Hi, this is a fresh install on a 1000HE asus "eeepc". It seems Jaunty is so "old" it can't even be upgraded. Any suggestions?  Command line reads:

```
laura@laura:~$ sudo apt-get update
Get:1 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release.gpg
Ign [http://www.array.org](http://www.array.org) jaunty Release.gpg                                    
Ign [http://www.array.org](http://www.array.org) jaunty/main Translation-en_US                         
Ign [http://www.array.org](http://www.array.org) jaunty Release                                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Ign [http://www.array.org](http://www.array.org) jaunty/main Packages                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Ign [http://www.array.org](http://www.array.org) jaunty/main Sources                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Ign [http://www.array.org](http://www.array.org) jaunty/main Packages                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Get:2 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Translation-en_US [73B]               
Ign [http://www.array.org](http://www.array.org) jaunty/main Sources                                   
96% [2 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Translation-en_US                       
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Get:3 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Translation-en_US [73B]           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
91% [3 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Translation-en_US                   
Err [http://www.array.org](http://www.array.org) jaunty/main Packages                                  
  404 Not Found
Get:4 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Translation-en_US [73B]            
Err [http://www.array.org](http://www.array.org) jaunty/main Sources                                   
  404 Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
86% [4 Translation-en_US bzip2 0] [Waiting for headers] [Waiting for headers] [bzip2: (stdin) is not a bzip2 file.
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
Get:5 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release                                    
Ign [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release                                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                           
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                     
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
  404 Not Found [IP: 91.189.91.24 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                       
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                     
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages                  
  404 Not Found [IP: 91.189.91.24 80]
Get:6 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages [73B]                        
89% [6 Packages bzip2 0] [Waiting for headers] [Waiting for headers] [Connectinbzip2: (stdin) is not a bzip2 file.
Err [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/main Packages                                
  Sub-process bzip2 returned an error code (2)
Ign [http://www.statux.org](http://www.statux.org) jaunty Release.gpg                                   
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages            
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                   
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources             
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages              
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources               
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages            
  404 Not Found [IP: 91.189.91.24 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources             
  404 Not Found [IP: 91.189.91.24 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Translation-en_US                        
Get:7 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages [73B]                    
90% [7 Packages bzip2 0] [Waiting for headers] [Connecting to finder.cox.net (9bzip2: (stdin) is not a bzip2 file.
Err [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/non-free Packages                            
  Sub-process bzip2 returned an error code (2)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
  404 Not Found [IP: 91.189.88.149 80]
Get:8 [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages [73B]                     
90% [8 Packages bzip2 0] [Waiting for headers] [Connecting to packages.medibuntbzip2: (stdin) is not a bzip2 file.
Err [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3/contrib Packages                             
  Sub-process bzip2 returned an error code (2)
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
  404 Not Found [IP: 91.189.88.149 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
  404 Not Found [IP: 91.189.88.149 80]
Ign [http://www.statux.org](http://www.statux.org) jaunty Release                                       
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages                                 
Ign [http://www.statux.org](http://www.statux.org) jaunty/main Packages                                 
Err [http://www.statux.org](http://www.statux.org) jaunty/main Packages                                 
  404 Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Fetched 2494B in 40s (62B/s)              
Reading package lists... Done
W: GPG error: [http://repos.eeebuntu.org](http://repos.eeebuntu.org) eb3 Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/Release.gpg](http://packages.medibuntu.org/dists/jaunty/Release.gpg)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/jaunty/free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/jaunty/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch [http://www.array.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.array.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://www.array.org/ubuntu/dists/jaunty/main/source/Sources](http://www.array.org/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://repos.eeebuntu.org/dists/eb3/main/binary-i386/Packages.bz2](http://repos.eeebuntu.org/dists/eb3/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://repos.eeebuntu.org/dists/eb3/non-free/binary-i386/Packages.bz2](http://repos.eeebuntu.org/dists/eb3/non-free/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://repos.eeebuntu.org/dists/eb3/contrib/binary-i386/Packages.bz2](http://repos.eeebuntu.org/dists/eb3/contrib/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources)  404 Not Found [IP: 91.189.88.149 80]

W: Failed to fetch [http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages](http://www.statux.org/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
laura@laura:~$
```

---

### Post by QIII on 2014-12-31
Hello!

Yes, Jaunty Jackalope (Ubuntu 9.04) is far, far past its End Of Life and is no longer supported.  The repositories have been moved, which is causing the 404 errors.

We would rather not have the volunteers on the Ubuntu Forums spending their limited time attempting to solve problems with such out-dated releases.

Furthermore, since Jaunty does not receive any updates -- including security updates -- it would be dangerous to use.

Please see the Staff's recommendations regarding what to do with unsupported releases [here]("http://ubuntuforums.org/showthread.php?t=2229730").

Since upgraded through several iterations of releases which are also EOL would be fraught with problems and probably ultimately unsuccessful, I would recommend a fresh installation of a currently supported release: 12.04, 14.04 or 14.10.  Be aware, however, that support for 14.10 will end in April, 2015.

---

### Post by sudodus on 2014-12-31
As can be seen in this link [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) Jaunty passed end of life in October 23, 2010, and you cannot expect that the repositories are maintained now.

Please try current versions of ***Lubuntu and Xubuntu 14.04.1 LTS*** (long time support version) supported until April 2017. While standard Ubuntu will be supported until 2019, I think the light-weight flavours Lubuntu and Xubuntu will work better with your old eeePC.

---

