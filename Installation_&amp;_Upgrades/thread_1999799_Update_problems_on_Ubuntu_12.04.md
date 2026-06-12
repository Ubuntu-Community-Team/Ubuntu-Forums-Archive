---
title: "Update problems on Ubuntu 12.04"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by zayid on 2012-06-08
Hello, i'm in a fix as my system refuses to update. i've tried several tricks like 
```

$ sudo -s[INDENT]  apt-get clean
  cd /var/lib/apt
  mv lists lists.old
  mkdir -p lists/partial
  apt-get clean
  apt-get update
[/INDENT]
```or

```
sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update 
sudo apt-get update

```But it has proven fruitless
 this is what i get after running the update command 
[HTML]root@yazid-T5101:~# sudo apt-get update
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise InRelease                  
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                 
Ign http://us.archive.ubuntu.com precise-updates InRelease           
Hit http://extras.ubuntu.com precise Release                                   
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release                               
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise-security InRelease                    
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise-proposed InRelease                    
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://ppa.launchpad.net precise InRelease                       
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:3 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:4 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Ign http://ppa.launchpad.net precise InRelease                                 
Get:5 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]        
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:6 http://us.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Ign http://ppa.launchpad.net precise InRelease                                 
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Get:8 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:9 http://ppa.launchpad.net precise Release.gpg [316 B]                     
Ign http://archive.canonical.com precise/partner Translation-en                
Get:10 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:11 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:12 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:13 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:14 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:15 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:16 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:17 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:18 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:19 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:20 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Get:21 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://us.archive.ubuntu.com precise Release                               
E: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: NODATA 2
[/HTML].

I would be very grateful for every assistance, thanks!

---

### Post by cortman on 2012-06-08
Are you behind a proxy or firewall?

---

### Post by zayid on 2012-06-08
No, i'm not. It is open no proxy or firewall

---

### Post by cortman on 2012-06-08
Ok, run this

```
sudo rm -r /var/lib/apt/lists/*
```

Then

```
sudo apt-get update
```

---

### Post by zayid on 2012-06-08
Did as you said but it still returned the NODATA 2 error

---

### Post by cortman on 2012-06-09
The problem is that it's not getting the GPG encryption key for a  certain repository- but the baffling thing is that it's not even getting  any data from the repository. This makes me wonder if changing your  server mirrors would fix that. Try doing that; you can go to the gear  icon in the upper right and select "Software Sources", I believe.

---

### Post by zayid on 2012-06-10
> **cortman said:**
> The problem is that it's not getting the GPG encryption key for a  certain repository- but the baffling thing is that it's not even getting  any data from the repository. This makes me wonder if changing your  server mirrors would fix that. Try doing that; you can go to the gear  icon in the upper right and select "Software Sources", I believe.

Tried changing the server like 3 times as shown below. 
Before i go ahead, I'll like to point out that it was initially on "Main Server" and used to give me errors so i changed as follows-

1 USA: I got the errors below
[HTML]W:GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29, E:GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: NODATA 2[/HTML]2 MIRRORS: I got the errors below
[HTML]W:GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29, E:GPG error: mirror://mirrors.ubuntu.com precise-updates Release: The following signatures were invalid: NODATA 2[/HTML]3 SOUTH AFRICA: I got the errors below
[HTML]W:GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29, E:GPG error: http://ftp.leg.uct.ac.za precise Release: The following signatures were invalid: NODATA 2[/HTML]Now the funny thing is I'm back to the "Main Server" and it actually completes the check for updates without errors but it also tells me "There are No Updates to Install" which i find funny cos it tells me i "Package Information Was Last Updated 9 Days Ago"  

now i decide to use ```
sudo apt-get update
``` via the terminal, and this is what i get-

[HTML]root@yazid-T5101:~# sudo apt-get update 
Ign http://archive.ubuntu.com precise InRelease                                
Ign http://dl.google.com stable InRelease                                      
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.ubuntu.com precise-updates InRelease                        
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.canonical.com precise InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Get:2 http://dl.google.com stable Release [1,347 B]                            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release.gpg                           
Ign http://archive.ubuntu.com precise-backports InRelease                      
Get:3 http://downloads.sourceforge.net all InRelease [1,891 B]                 
Ign http://downloads.sourceforge.net all InRelease                             
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release.gpg                           
Get:4 http://dl.google.com stable/main i386 Packages [1,254 B]                 
Hit http://extras.ubuntu.com precise/main Sources                              
Ign http://archive.ubuntu.com precise-security InRelease                       
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://downloads.sourceforge.net all/main i386 Packages/DiffIndex          
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.canonical.com precise Release                               
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://archive.ubuntu.com precise-proposed InRelease                       
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise Release                               
Ign http://downloads.sourceforge.net all/main TranslationIndex                 
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:5 http://archive.ubuntu.com precise Release.gpg [198 B]                    
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise/partner Sources                       
Get:6 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:7 http://archive.ubuntu.com precise-backports Release.gpg [198 B]          
Ign http://archive.canonical.com precise/partner TranslationIndex              
Ign http://ppa.launchpad.net precise InRelease                                 
Get:8 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Hit http://archive.canonical.com precise/partner Sources                       
Ign http://ppa.launchpad.net precise InRelease                                 
Get:9 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]           
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:10 http://archive.ubuntu.com precise Release [49.6 kB]                     
Err http://archive.ubuntu.com precise Release                                  
  
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:11 http://archive.ubuntu.com precise-updates Release [49.6 kB]             
Err http://archive.ubuntu.com precise-updates Release                          
  
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable/main Translation-en_US                         
Get:12 http://archive.ubuntu.com precise-backports Release [49.6 kB]           
Err http://archive.ubuntu.com precise-backports Release                        
  
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://dl.google.com stable/main Translation-en                            
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise InRelease                                 
Get:13 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Err http://archive.ubuntu.com precise-security Release                         
  
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise InRelease                                 
Get:14 http://archive.ubuntu.com precise-proposed Release [49.6 kB]            
Err http://archive.ubuntu.com precise-proposed Release                         
  
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://downloads.sourceforge.net all/main i386 Packages                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://ppa.launchpad.net precise Release.gpg                               
Ign http://downloads.sourceforge.net all/main Translation-en_US                
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://downloads.sourceforge.net all/main Translation-en                   
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:15 http://ppa.launchpad.net precise Release.gpg [316 B]                    
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://archive.canonical.com precise/partner Translation-en_US             
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://archive.canonical.com precise/partner Translation-en                
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                 
Ign http://ppa.launchpad.net precise Release                                 
Hit http://ppa.launchpad.net precise Release
Hit http://ppa.launchpad.net precise Release                                 
Hit http://ppa.launchpad.net precise Release                                 
Get:16 http://ppa.launchpad.net precise Release [11.9 kB]                    
Err http://ppa.launchpad.net precise Release                                   
  
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Hit http://ppa.launchpad.net precise/main Sources
Hit http://ppa.launchpad.net precise/main i386 Packages
Ign http://ppa.launchpad.net precise/main TranslationIndex
Err http://ppa.launchpad.net precise/main Sources
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 17.9 kB in 3min 26s (86 B/s)
Reading package lists... Done
W: GPG error: http://downloads.sourceforge.net all InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CCC158AFC1289A29
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-updates Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-backports Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-security Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com precise-proposed Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: NODATA 2

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-backports/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-security/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise-proposed/Release  

W: Failed to fetch http://ppa.launchpad.net/noobslab/themes/ubuntu/dists/precise/Release  

W: Failed to fetch http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gnomenu-team/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Some index files failed to download. They have been ignored, or old ones used instead.
[/HTML]

---

### Post by Old_Grey_Wolf on 2012-06-10
You are missing the GPG Key. To get it enter these commands ```
gpg --keyserver keyserver.ubuntu.com --recv CCC158AFC1289A29

gpg --export --armor CCC158AFC1289A29 | sudo apt-key add -
```

---

### Post by zayid on 2012-06-10
Did the GPG key import stuff but it still isn't working. Just to say thanks guys for all the ideas pls keep them coming

---

### Post by Old_Grey_Wolf on 2012-06-10
Try these commands ```
sudo rm /var/lib/apt/lists/* -vf

sudo apt-get clean

sudo apt-get update
```

---

### Post by zayid on 2012-06-11
Followed the instruction and it removed a lot of \'var/lib/apt..............................  ppas. So i use the clean command then update and i get 
[HTML]Ign http://dl.google.com stable InRelease                                     
Ign http://archive.canonical.com precise InRelease                            
Ign http://archive.ubuntu.com precise InRelease                               
Ign http://extras.ubuntu.com precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Get:1 http://dl.google.com stable Release.gpg [198 B]                         
Ign http://ppa.launchpad.net precise InRelease                                
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]                     
Ign http://ppa.launchpad.net precise InRelease                                
Get:3 http://extras.ubuntu.com precise Release [11.9 kB]                      
Ign http://archive.ubuntu.com precise-updates InRelease                       
Ign http://archive.canonical.com precise InRelease                            
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Get:4 http://dl.google.com stable Release [1,347 B]                           
Get:5 http://archive.canonical.com precise Release.gpg [198 B]                
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://archive.ubuntu.com precise-backports InRelease                     
Ign http://ppa.launchpad.net precise InRelease                                
Get:6 http://downloads.sourceforge.net all InRelease [1,891 B]                
Get:7 http://archive.canonical.com precise Release.gpg [198 B]                
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Get:8 http://archive.canonical.com precise Release [7,078 B]                  
Get:9 http://dl.google.com stable/main i386 Packages [1,254 B]                
Ign http://archive.ubuntu.com precise-security InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Get:10 http://extras.ubuntu.com precise/main Sources [747 B]                  
Ign http://archive.ubuntu.com precise-proposed InRelease                      
Ign http://ppa.launchpad.net precise InRelease                                
Get:11 http://extras.ubuntu.com precise/main i386 Packages [885 B]            
Ign http://dl.google.com stable/main TranslationIndex                         
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://extras.ubuntu.com precise/main TranslationIndex                    
Ign http://ppa.launchpad.net precise InRelease                                
Get:12 http://archive.ubuntu.com precise Release.gpg [198 B]                  
Get:13 http://downloads.sourceforge.net all/main i386 Packages [847 B]        
Ign http://ppa.launchpad.net precise InRelease                                
Get:14 http://archive.canonical.com precise Release [7,078 B]                 
Ign http://ppa.launchpad.net precise InRelease                                
Ign http://ppa.launchpad.net precise InRelease                                
Get:15 http://archive.ubuntu.com precise-updates Release.gpg [198 B]          
Get:16 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Ign http://downloads.sourceforge.net all/main TranslationIndex                
Get:17 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:18 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:19 http://archive.ubuntu.com precise-backports Release.gpg [198 B]        
Get:20 http://archive.canonical.com precise/partner Sources [3,430 B]         
Get:21 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:22 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Ign http://extras.ubuntu.com precise/main Translation-en_US                   
Ign http://ppa.launchpad.net precise Release.gpg                              
Ign http://extras.ubuntu.com precise/main Translation-en                      
Get:23 http://archive.ubuntu.com precise-security Release.gpg [198 B]         
Get:24 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:25 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:26 http://archive.canonical.com precise/partner i386 Packages [4,982 B]   
Get:27 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:28 http://archive.ubuntu.com precise-proposed Release.gpg [198 B]         
Get:29 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:30 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:31 http://archive.ubuntu.com precise Release [49.6 kB]                    
Get:32 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:33 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:34 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Ign http://archive.canonical.com precise/partner TranslationIndex             
Get:35 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:36 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Ign http://dl.google.com stable/main Translation-en_US                        
Get:37 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Get:38 http://archive.canonical.com precise/partner Sources [3,430 B]         
Get:39 http://ppa.launchpad.net precise Release.gpg [316 B]                   
Ign http://dl.google.com stable/main Translation-en                           
Get:40 http://ppa.launchpad.net precise Release [11.9 kB]                     
Get:41 http://archive.canonical.com precise/partner i386 Packages [4,982 B]   
Ign http://downloads.sourceforge.net all/main Translation-en_US               
Ign http://downloads.sourceforge.net all/main Translation-en                  
Ign http://archive.canonical.com precise/partner TranslationIndex             
Err http://ppa.launchpad.net precise Release                                  
  
Get:42 http://ppa.launchpad.net precise Release [11.9 kB]                     
Ign http://ppa.launchpad.net precise Release                                  
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: NODATA 2

E: GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: NODATA 2
[/HTML]

---

### Post by zayid on 2012-06-11
I tried to update through the update manager and got these errors
[HTML]W:GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: BADSIG 77589CABF0B5D826 Launchpad antigone, E:GPG error: http://ppa.launchpad.net precise Release: The following signatures were invalid: NODATA 2[/HTML]

---

### Post by velkymx on 2012-06-13
This worked for me to fix it:

try running:

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf > /dev/null

Then try:

sudo apt-get update

Again....

---

