---
title: "404 errors from apt-get update"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by qcdisciple on 2011-10-08
I'm using natty 64 bit on a lenovo laptop.  I tried to install google chrome by downloading the deb and opening it in the Software Center.  It said package files didn't download.  I looked online and decided to try to fix  my sources.list file.  I used a generator to make a new file with just the basic repositories.  When I tried to update, this came out:```
Get:1 http://packages.medibuntu.org natty InRelease [7,092 B]
Ign http://archive.ubuntu.com main InRelease                
Ign http://archive.ubuntu.com -security InRelease   
Ign http://archive.ubuntu.com -updates InRelease
Ign http://packages.medibuntu.org natty InRelease
Ign http://archive.ubuntu.com main Release.gpg
Ign http://archive.ubuntu.com -security Release.gpg       
Ign http://archive.ubuntu.com -updates Release.gpg        
Ign http://archive.ubuntu.com main Release                
Ign http://packages.medibuntu.org natty/free Sources/DiffIndex
Ign http://archive.ubuntu.com -security Release
Ign http://archive.ubuntu.com -updates Release                                 
Ign http://packages.medibuntu.org natty/non-free Sources/DiffIndex             
Ign http://archive.ubuntu.com main/restricted TranslationIndex
Ign http://archive.ubuntu.com main/universe TranslationIndex
Ign http://packages.medibuntu.org natty/free amd64 Packages/DiffIndex          
Ign http://archive.ubuntu.com -security/main TranslationIndex                  
Ign http://archive.ubuntu.com -security/restricted TranslationIndex            
Ign http://archive.ubuntu.com -security/universe TranslationIndex
Ign http://archive.ubuntu.com -updates/main TranslationIndex
Ign http://archive.ubuntu.com -updates/restricted TranslationIndex
Ign http://archive.ubuntu.com -updates/universe TranslationIndex
Ign http://packages.medibuntu.org natty/non-free amd64 Packages/DiffIndex
Ign http://packages.medibuntu.org natty/free TranslationIndex
Ign http://packages.medibuntu.org natty/non-free TranslationIndex
Hit http://packages.medibuntu.org natty/free Sources                           
Hit http://packages.medibuntu.org natty/non-free Sources                       
Hit http://packages.medibuntu.org natty/free amd64 Packages
Hit http://packages.medibuntu.org natty/non-free amd64 Packages
Err http://archive.ubuntu.com main/restricted Sources                          
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com main/universe Sources                            
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com main/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com main/universe amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/main Sources
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/restricted Sources                     
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/universe Sources                       
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/main amd64 Packages                    
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/restricted amd64 Packages              
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -security/universe amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/main Sources
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/restricted Sources 
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/universe Sources   
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/main amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Err http://archive.ubuntu.com -updates/universe amd64 Packages
  404  Not Found [IP: 91.189.92.170 80]
Ign http://archive.ubuntu.com main/restricted Translation-en_US
Ign http://archive.ubuntu.com main/restricted Translation-en
Ign http://archive.ubuntu.com main/universe Translation-en_US
Ign http://archive.ubuntu.com main/universe Translation-en
Ign http://archive.ubuntu.com -security/main Translation-en_US
Ign http://archive.ubuntu.com -security/main Translation-en
Ign http://archive.ubuntu.com -security/restricted Translation-en_US
Ign http://archive.ubuntu.com -security/restricted Translation-en
Ign http://archive.ubuntu.com -security/universe Translation-en_US
Ign http://archive.ubuntu.com -security/universe Translation-en
Ign http://archive.ubuntu.com -updates/main Translation-en_US
Ign http://archive.ubuntu.com -updates/main Translation-en
Ign http://archive.ubuntu.com -updates/restricted Translation-en_US
Ign http://archive.ubuntu.com -updates/restricted Translation-en
Ign http://archive.ubuntu.com -updates/universe Translation-en_US
Ign http://archive.ubuntu.com -updates/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 1 B in 7s (0 B/s)                                                      
W: GPG error: http://packages.medibuntu.org natty InRelease: Unknown error executing gpgv
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/main/restricted/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/main/universe/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/main/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/main/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/main/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/restricted/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/universe/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-security/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/main/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/restricted/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/universe/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/main/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/restricted/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/-updates/universe/binary-amd64/Packages  404  Not Found [IP: 91.189.92.170 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by Rubi1200 on 2011-10-08
Hi and welcome to the forums :)

You may need to try switching to the Main Server from whatever is set as your current download mirror. 

You can do this either in Synaptic or the Ubuntu Software Center.

---

### Post by qcdisciple on 2011-10-16
It worked at first, but when I tried to upgrade to 11.10 it said that it couldn't authenticate a bunch of packages.

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

[http://www.upubuntu.com/2011/07/remo...e-404-not.html](http://www.upubuntu.com/2011/07/remo...e-404-not.html)

---

### Post by qcdisciple on 2011-11-11
I'm still having trouble.  There is an error authenticating packages when I try to update or upgrade.  Look at the sceenshot to see exactly what happens.

---

### Post by oldos2er on 2011-11-11
Can you run ```
sudo apt-get update
``` in a terminal, and post the output here?

---

### Post by qcdisciple on 2011-11-11
I've tried it a bunch of times before.  I always get the same errors.
```
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [189 B]                          
Get:2 http://dl.google.com stable Release [2,544 B]                            
Ign http://archive.ubuntu.com natty InRelease                                  
Ign http://archive.ubuntu.com natty-updates InRelease                          
Ign http://archive.canonical.com natty InRelease                               
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://dl.google.com stable Release                                        
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://dl.google.com stable/non-free amd64 Packages/DiffIndex              
Ign http://dl.google.com stable/non-free TranslationIndex                      
Get:3 http://archive.ubuntu.com natty Release.gpg [198 B]                      
Get:4 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:5 http://archive.canonical.com natty Release.gpg [198 B]                   
Get:6 http://dl.google.com stable/non-free amd64 Packages [1,025 B]            
Get:7 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:8 http://ppa.launchpad.net natty Release.gpg [316 B]                       
Get:9 http://archive.ubuntu.com natty-updates Release.gpg [198 B]              
Get:10 http://packages.medibuntu.org natty InRelease [7,092 B]                 
Ign http://packages.medibuntu.org natty InRelease                              
Get:11 http://security.ubuntu.com natty-security Release [31.4 kB]             
Get:12 http://archive.canonical.com natty Release [5,916 B]                    
Ign http://archive.canonical.com natty Release                                 
Ign http://ppa.launchpad.net natty Release.gpg                                 
Get:13 http://ppa.launchpad.net natty Release [9,733 B]                        
Ign http://ppa.launchpad.net natty Release                                     
Get:14 http://archive.ubuntu.com natty Release [39.8 kB]                       
Ign http://archive.canonical.com natty/partner Sources/DiffIndex               
Get:15 http://ppa.launchpad.net natty Release [9,766 B]                        
Ign http://archive.ubuntu.com natty Release                                    
Ign http://ppa.launchpad.net natty Release                                     
Ign http://packages.medibuntu.org natty/free Sources/DiffIndex                 
Ign http://ppa.launchpad.net natty Release                                     
Get:16 http://archive.ubuntu.com natty-updates Release [31.4 kB]               
Ign http://archive.ubuntu.com natty-updates Release                            
Ign http://archive.canonical.com natty/partner amd64 Packages/DiffIndex        
Ign http://archive.canonical.com natty/partner TranslationIndex                
Ign http://security.ubuntu.com natty-security Release                          
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                      
Ign http://ppa.launchpad.net natty/main amd64 Packages/DiffIndex               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty/main Sources/DiffIndex                     
Ign http://archive.ubuntu.com natty/universe Sources/DiffIndex                 
Ign http://archive.ubuntu.com natty/restricted Sources/DiffIndex               
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://archive.canonical.com natty/partner Sources                         
Ign http://dl.google.com stable/non-free Translation-en                        
Ign http://security.ubuntu.com natty-security/universe Sources/DiffIndex       
Ign http://packages.medibuntu.org natty/non-free Sources/DiffIndex             
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                      
Ign http://ppa.launchpad.net natty/main amd64 Packages/DiffIndex               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty/multiverse Sources/DiffIndex               
Ign http://archive.ubuntu.com natty/main amd64 Packages/DiffIndex              
Ign http://archive.ubuntu.com natty/universe amd64 Packages/DiffIndex          
Ign http://archive.ubuntu.com natty/restricted amd64 Packages/DiffIndex        
Ign http://archive.ubuntu.com natty/multiverse amd64 Packages/DiffIndex        
Ign http://archive.ubuntu.com natty/main TranslationIndex                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                  
Hit http://archive.canonical.com natty/partner amd64 Packages                  
Ign http://security.ubuntu.com natty-security/main Sources/DiffIndex           
Ign http://security.ubuntu.com natty-security/multiverse Sources/DiffIndex     
Ign http://security.ubuntu.com natty-security/restricted Sources/DiffIndex     
Ign http://security.ubuntu.com natty-security/universe amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main amd64 Packages/DiffIndex    
Ign http://security.ubuntu.com natty-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://ppa.launchpad.net natty/main Sources/DiffIndex                      
Ign http://ppa.launchpad.net natty/main amd64 Packages/DiffIndex               
Ign http://ppa.launchpad.net natty/main TranslationIndex                       
Ign http://archive.ubuntu.com natty-updates/universe Sources/DiffIndex         
Hit http://ppa.launchpad.net natty/main Sources                                
Ign http://archive.ubuntu.com natty-updates/main Sources/DiffIndex             
Ign http://archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex       
Ign http://archive.ubuntu.com natty-updates/restricted Sources/DiffIndex       
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://archive.ubuntu.com natty-updates/universe amd64 Packages/DiffIndex  
Ign http://archive.ubuntu.com natty-updates/main amd64 Packages/DiffIndex      
Ign http://archive.ubuntu.com natty-updates/multiverse amd64 Packages/DiffIndex
Ign http://archive.ubuntu.com natty-updates/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Get:17 http://security.ubuntu.com natty-security/universe Sources [13.7 kB]    
Get:18 http://security.ubuntu.com natty-security/main Sources [76.0 kB]        
Ign http://packages.medibuntu.org natty/free amd64 Packages/DiffIndex          
Hit http://ppa.launchpad.net natty/main Sources                                
Hit http://ppa.launchpad.net natty/main amd64 Packages                         
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex          
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/universe Sources                           
Hit http://archive.ubuntu.com natty/restricted Sources                         
Hit http://archive.ubuntu.com natty/multiverse Sources                         
Hit http://archive.ubuntu.com natty/main amd64 Packages                        
Hit http://archive.ubuntu.com natty/universe amd64 Packages                    
Hit http://archive.ubuntu.com natty/restricted amd64 Packages                  
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages                  
Ign http://packages.medibuntu.org natty/non-free amd64 Packages/DiffIndex      
Hit http://archive.ubuntu.com natty-updates/universe Sources                   
Hit http://archive.ubuntu.com natty-updates/main Sources                       
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                 
Get:19 http://security.ubuntu.com natty-security/multiverse Sources [652 B]    
Get:20 http://security.ubuntu.com natty-security/restricted Sources [14 B]     
Get:21 http://security.ubuntu.com natty-security/universe amd64 Packages [51.9 kB]
Hit http://archive.ubuntu.com natty-updates/restricted Sources                 
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages            
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages                
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages          
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages          
Get:22 http://security.ubuntu.com natty-security/main amd64 Packages [214 kB]  
Ign http://packages.medibuntu.org natty/free TranslationIndex                  
Ign http://packages.medibuntu.org natty/non-free TranslationIndex              
Ign http://archive.canonical.com natty/partner Translation-en_US               
Get:23 http://security.ubuntu.com natty-security/multiverse amd64 Packages [1,928 B]
Get:24 http://security.ubuntu.com natty-security/restricted amd64 Packages [14 B]
Ign http://archive.canonical.com natty/partner Translation-en                  
Hit http://packages.medibuntu.org natty/free Sources                           
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en               
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Hit http://packages.medibuntu.org natty/non-free Sources             
Err http://ppa.launchpad.net natty/main Sources                      
  404  Not Found
Err http://ppa.launchpad.net natty/main amd64 Packages               
  404  Not Found
Ign http://ppa.launchpad.net natty/main Translation-en_US                      
Ign http://ppa.launchpad.net natty/main Translation-en                         
Hit http://packages.medibuntu.org natty/free amd64 Packages          
Hit http://packages.medibuntu.org natty/non-free amd64 Packages      
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://archive.ubuntu.com natty/main Translation-en_US                     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US     
Ign http://archive.ubuntu.com natty/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US
Ign http://security.ubuntu.com natty-security/restricted Translation-en
Ign http://security.ubuntu.com natty-security/universe Translation-en_US
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://archive.ubuntu.com natty/restricted Translation-en_US               
Ign http://archive.ubuntu.com natty/restricted Translation-en                  
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://packages.medibuntu.org natty/free Translation-en_US                 
Ign http://packages.medibuntu.org natty/free Translation-en                    
Ign http://packages.medibuntu.org natty/non-free Translation-en_US             
Ign http://packages.medibuntu.org natty/non-free Translation-en                
Fetched 394 kB in 7s (52.5 kB/s)                                               
W: GPG error: http://dl.google.com stable Release: Unknown error executing gpgv
W: GPG error: http://packages.medibuntu.org natty InRelease: Unknown error executing gpgv
W: GPG error: http://archive.canonical.com natty Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net natty Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com natty Release: Unknown error executing gpgv
W: GPG error: http://ppa.launchpad.net natty Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com natty-updates Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com natty-security Release: Unknown error executing gpgv
W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by raja.genupula on 2011-11-11
[http://ubuntuforums.org/showthread.php?t=1484848](http://ubuntuforums.org/showthread.php?t=1484848)

---

### Post by qcdisciple on 2011-11-12
I can't believe it, but it worked!  Thanks to everyone who answered!

---

### Post by Rubi1200 on 2011-11-12
Nice one! Glad you got things working now :)

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by Solomoriah on 2011-11-14
> **subehsharma said:**
> To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
And at this point, I get the usual long list of updates, including these interesting lines:

> W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

So... what now?

---

### Post by Elfy on 2011-11-14
Disable the PPAs that do not have oneiric versions available.

[http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/](http://ppa.launchpad.net/lkjoel/fix404/ubuntu/dists/)

---

