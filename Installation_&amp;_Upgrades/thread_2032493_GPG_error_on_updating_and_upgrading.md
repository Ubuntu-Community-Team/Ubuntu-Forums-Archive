---
title: "GPG error on updating and upgrading"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by HonarDust on 2012-07-24
Hi! 
I'm using kubuntu 12.04!
 Today when i run Update, i ran in to this error. I put the full logs so you can see all:
```
amirhossein@AHbook:~$ sudo aptitude update
Ign http://security.ubuntu.com precise-security InRelease                                                       
Ign http://extras.ubuntu.com precise InRelease                                            
Ign http://archive.canonical.com precise InRelease                                         
Ign http://ppa.launchpad.net precise InRelease                                             
Get: 1 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                     
Hit http://extras.ubuntu.com precise Release.gpg                                                                       
Get: 2 http://security.ubuntu.com precise-security Release [49.6 kB]                       
Hit http://archive.canonical.com precise Release.gpg                                                                 
Get: 3 http://ppa.launchpad.net precise Release.gpg [316 B]                                          
Hit http://archive.canonical.com precise Release                                                                                  
Hit http://ppa.launchpad.net precise Release                                                         
Ign http://ppa.launchpad.net precise Release                                   
Hit http://archive.canonical.com precise/partner Sources                                             
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                                          
Hit http://extras.ubuntu.com precise Release                                                                            
Get: 4 http://security.ubuntu.com precise-security/main Sources [30.2 kB]                   
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex                                                    
Hit http://extras.ubuntu.com precise/main Sources                                                    
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                                         
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex                                    
Hit http://archive.canonical.com precise/partner amd64 Packages                                      
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                        
Hit http://archive.canonical.com precise/partner i386 Packages                              
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                              
Get: 5 http://security.ubuntu.com precise-security/restricted Sources [14 B]                
Ign http://archive.canonical.com precise/partner TranslationIndex                                                                                 
Get: 6 http://security.ubuntu.com precise-security/universe Sources [7,849 B]               
Hit http://ppa.launchpad.net precise/main Sources                                                                                                     
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                     
Get: 7 http://security.ubuntu.com precise-security/multiverse Sources [713 B]               
Get: 8 http://security.ubuntu.com precise-security/main amd64 Packages [96.7 kB]                                    
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                
Ign http://ir.archive.ubuntu.com precise InRelease                                                                         
Ign http://ir.archive.ubuntu.com precise-updates InRelease                                                                       
Ign http://ir.archive.ubuntu.com precise-backports InRelease                                                                     
Get: 9 http://ir.archive.ubuntu.com precise Release.gpg [198 B]                                       
Get: 10 http://ir.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                           
Get: 11 http://ir.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                                                     
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                                                 
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                                                    
Get: 12 http://ir.archive.ubuntu.com precise Release [49.6 kB]                                                                                                              
Ign http://ppa.launchpad.net precise/main Translation-en_US                                                                                                                 
Ign http://archive.canonical.com precise/partner Translation-en_US                                                                                                          
Ign http://ppa.launchpad.net precise/main Translation-en                                                                                                                    
Ign http://archive.canonical.com precise/partner Translation-en                                                                                                             
Get: 13 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]                                                                                        
Get: 14 http://security.ubuntu.com precise-security/universe amd64 Packages [24.2 kB]                                                                                       
Get: 15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]                                                                                     
Get: 16 http://security.ubuntu.com precise-security/main i386 Packages [99.6 kB]                                                                                            
Get: 17 http://ir.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                                                      
Get: 18 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]                                                                                         
Get: 19 http://security.ubuntu.com precise-security/universe i386 Packages [24.4 kB]                                                                                        
Get: 20 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]                                                                                      
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                                                 
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                                                 
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                                   
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                         
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                                   
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                                     
Get: 21 http://ir.archive.ubuntu.com precise-backports Release [49.6 kB]                                                                                                    
Get: 22 http://ir.archive.ubuntu.com precise/main Sources [934 kB]                                                                                                          
Get: 23 http://ir.archive.ubuntu.com precise/restricted Sources [5,470 B]                                                                                                   
Get: 24 http://ir.archive.ubuntu.com precise/universe Sources [5,019 kB]                                                                                                    
Get: 25 http://ir.archive.ubuntu.com precise/multiverse Sources [155 kB]                                                                                                    
Get: 26 http://ir.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                                                                                                 
Get: 27 http://ir.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                                                                                            
Get: 28 http://ir.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                                                                                             
Get: 29 http://ir.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                                                                                             
Get: 30 http://ir.archive.ubuntu.com precise/main i386 Packages [1,274 kB]                                                                                                  
Get: 31 http://ir.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]                                                                                             
Get: 32 http://ir.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get: 33 http://ir.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]                                                                                              
Hit http://ir.archive.ubuntu.com precise/main TranslationIndex                                                                                                              
Hit http://ir.archive.ubuntu.com precise/multiverse TranslationIndex                                                                                                        
Hit http://ir.archive.ubuntu.com precise/restricted TranslationIndex                                                                                                        
Hit http://ir.archive.ubuntu.com precise/universe TranslationIndex                                                                                                          
Get: 34 http://ir.archive.ubuntu.com precise-updates/main Sources [134 kB]                                                                                                  
Get: 35 http://ir.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]                                                                                           
Get: 36 http://ir.archive.ubuntu.com precise-updates/universe Sources [38.2 kB]                                                                                             
Get: 37 http://ir.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]                                                                                           
Get: 38 http://ir.archive.ubuntu.com precise-updates/main amd64 Packages [331 kB]                                                                                           
Get: 39 http://ir.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]                                                                                    
Get: 40 http://ir.archive.ubuntu.com precise-updates/universe amd64 Packages [97.2 kB]                                                                                      
Get: 41 http://ir.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]                                                                                    
Get: 42 http://ir.archive.ubuntu.com precise-updates/main i386 Packages [334 kB]                                                                                            
Get: 43 http://ir.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]                                                                                     
Get: 44 http://ir.archive.ubuntu.com precise-updates/universe i386 Packages [97.7 kB]                                                                                       
Get: 45 http://ir.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]                                                                                     
Hit http://ir.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                                      
Hit http://ir.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                                
Hit http://ir.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                                
Hit http://ir.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                                  
Get: 46 http://ir.archive.ubuntu.com precise-backports/main Sources [2,422 B]                                                                                               
Get: 47 http://ir.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                                            
Get: 48 http://ir.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]                                                                                           
Get: 49 http://ir.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]                                                                                         
Get: 50 http://ir.archive.ubuntu.com precise-backports/main amd64 Packages [1,945 B]                                                                                        
Get: 51 http://ir.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                                                     
Get: 52 http://ir.archive.ubuntu.com precise-backports/universe amd64 Packages [11.1 kB]                                                                                    
Get: 53 http://ir.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]                                                                                    
Get: 54 http://ir.archive.ubuntu.com precise-backports/main i386 Packages [1,941 B]                                                                                         
Get: 55 http://ir.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                                      
Get: 56 http://ir.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]                                                                                     
Get: 57 http://ir.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]                                                                                     
Hit http://ir.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                                    
Hit http://ir.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                              
Hit http://ir.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                              
Hit http://ir.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                                
Hit http://ir.archive.ubuntu.com precise/main Translation-en                                                                                                                
Hit http://ir.archive.ubuntu.com precise/multiverse Translation-en                                                                                                          
Hit http://ir.archive.ubuntu.com precise/restricted Translation-en                                                                                                          
Hit http://ir.archive.ubuntu.com precise/universe Translation-en                                                                                                            
Hit http://ir.archive.ubuntu.com precise-updates/main Translation-en                                                                                                        
Hit http://ir.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                  
Hit http://ir.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                  
Hit http://ir.archive.ubuntu.com precise-updates/universe Translation-en                                                                                                    
Hit http://ir.archive.ubuntu.com precise-backports/main Translation-en                                                                                                      
Hit http://ir.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                                
Hit http://ir.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                                
Hit http://ir.archive.ubuntu.com precise-backports/universe Translation-en                                                                                                  
Fetched 20.1 MB in 18min 58s (17.6 kB/s)                                                                                                                                    
W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DD90B5460AD95754

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DD90B5460AD95754

```Ok and when i run upgrade after that it shows this error:
```
amirhossein@AHbook:~$ sudo aptitude upgrade
[sudo] password for amirhossein: 
Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.

```So where is the the problem? How can i fix it?
I'm sorry if i put the topic on wrong section. Ubuntu forum is a little confusing.

---

### Post by dino99 on 2012-07-24
Please open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type or better copy and paste a row atime then press enter:

gpg --keyserver keyserver.ubuntu.com --recv DD90B5460AD95754
gpg --export --armor DD90B5460AD95754 | sudo apt-key add -

sudo apt-get update

give your user password when requested, you don't see nothing when you type it, then press enter.

Hope this helps

---

### Post by HonarDust on 2012-07-24
> **dino99 said:**
> Please open a Terminal from the menu Applications &#8594; Accessories &#8594; Terminal and type or better copy and paste a row atime then press enter:

gpg --keyserver keyserver.ubuntu.com --recv DD90B5460AD95754
gpg --export --armor DD90B5460AD95754 | sudo apt-key add -

sudo apt-get update

give your user password when requested, you don't see nothing when you type it, then press enter.

Hope this helps

This helped the first problem. Tnx for that. But the second one still stood.
```
amirhossein@AHbook:~$ sudo aptitude upgrade
[sudo] password for amirhossein: 
Resolving dependencies...                
Unable to resolve dependencies for the upgrade: no solution found.
Unable to safely resolve dependencies, try running with --full-resolver.

```

---

### Post by dino99 on 2012-07-24
i dont like aptitude, prefer apt-get. Copy/paste each line at a time into a terminal, then hit Enter key:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

---

### Post by HonarDust on 2012-07-24
> **dino99 said:**
> i dont like aptitude, prefer apt-get. Copy/paste each line at a time into a terminal, then hit Enter key:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f

Tnx apt-get successfully upgraded. But aptitude still have the same problem.

---

### Post by dino99 on 2012-07-24
> **HonarDust said:**
> Tnx apt-get successfully upgraded. But aptitude still have the same problem.

you're right it should work, but it dont; so its up to you to make your choice :P

---

### Post by HonarDust on 2012-07-24
> **dino99 said:**
> you're right it should work, but it dont; so its up to you to make your choice :P
Well the only difference i find between these two, was aptitude is faster to type.:D

---

### Post by Zorael on 2012-07-24
Try **full-upgrade** instead of just **upgrade**. A normal (safe) upgrade will never remove packages, but a full will. So don't proceed if it says it wants to remove lots and lots.

```
$ sudo aptitude full-upgrade
```

Also, is this a 64-bit installation?

---

### Post by HonarDust on 2012-07-24
> **Zorael said:**
> Try **full-upgrade** instead of just **upgrade**. A normal (safe) upgrade will never remove packages, but a full will. So don't proceed if it says it wants to remove lots and lots.

```
$ sudo aptitude full-upgrade
```Also, is this a 64-bit installation?
It worked just fine! Tnx a lot. And yes. I use 64bit.

---

### Post by Zorael on 2012-07-24
Okay.

As a slight warning; if aptitude suddenly wants to remove pretty much your whole system you may have hit [bug #831768](https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/831768).

I normally prefer aptitude because of its superior dependency resolving, but until they sort out that bug I'm falling back to apt-get.

---

