---
title: "videolan Translation-en_AU Ubuntu general update slowed system"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by greg25 on 2013-12-09
Here goes with my first post.

Encountered some problms trying to install minecraft on two near identical machines running Ubuntu.  The simple plan was to update Ubuntu from the terminal and then install minecraft using the Minecraft Installer method.

This worked well for the first machine.  The second machine throws up some errors which you can see at the end of the following log of sudo apt-get update.  This machine has also substantially slower browsing since the recent update attempts.  Any pointers would be appreciated.

hamish@hamish-HP-Pavilion-dv2000-GG176PA-ABG:~$ sudo apt-get clean
[sudo] password for hamish: 
hamish@hamish-HP-Pavilion-dv2000-GG176PA-ABG:~$ sudo apt-get update
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security Release.gpg [198 B]        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security Release                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Sources                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Sources 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/main Sources                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/restricted Sources           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/universe Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/multiverse Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/main i386 Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/restricted i386 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/universe i386 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/multiverse i386 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/main TranslationIndex        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/multiverse TranslationIndex  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/restricted TranslationIndex  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/universe TranslationIndex    
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en_AU                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/main Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise/universe Translation-en
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/main Translation-en          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/multiverse Translation-en    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/restricted Translation-en    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-security/universe Translation-en      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources/DiffIndex                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Get:6 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release.gpg [287 B]    
Hit [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                          
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_AU            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Get:7 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_AU                                                                            
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages/DiffIndex                                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                                                                               
Get:8 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU                                                                                      
Get:9 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en                                                                                         
Hit [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Packages
Get:10 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU
Get:11 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en
Get:12 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU
Get:13 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU  
Get:14 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en
Get:15 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU
Err [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en_AU
  Could not connect passive socket.
Get:16 [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en
Ign [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Translation-en
Fetched 1,387 B in 5min 0s (4 B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7375AF8BDA39203D
W: GPG error: [ftp://ftp.videolan.org](ftp://ftp.videolan.org) ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6BCA5E4DB84288D9
W: Failed to fetch [ftp://ftp.videolan.org/pub/debian/stable/./en_AU](ftp://ftp.videolan.org/pub/debian/stable/./en_AU)  Could not connect passive socket.

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

