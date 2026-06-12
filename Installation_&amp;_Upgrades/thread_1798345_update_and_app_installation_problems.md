---
title: "update and app installation problems"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by mayurg on 2011-07-06
hello everyone,
i just installed ubuntu 10.10. I tried to update by using the update manager but it could not update. Also if I want to install apps by the Ubuntu Software Center, (I am installing VLC media player), no apps could be installed. The following error is found when I use the command sudo apt-get update

```
mayur@mayur-Studio-1555:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg                          
  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en       
  Unable to connect to archive.canonical.com:http:
Err [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN    
  Unable to connect to archive.canonical.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                              
  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN           
  Unable to connect to extras.ubuntu.com:http:
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick Release                              
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                                  
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Ign [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources                      
  Unable to connect to archive.canonical.com:http:
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
Err [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages                
  Unable to connect to archive.canonical.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources                             
  Unable to connect to extras.ubuntu.com:http:
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages                       
  Unable to connect to extras.ubuntu.com:http:
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages/DiffIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources              
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages        
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources                  
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages            
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages      
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg                             
  Could not connect to archive.ubuntu.com:80 (91.189.92.169). - connect (110: Connection timed out) [IP: 91.189.92.169 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release.gpg                          
  Could not connect to in.archive.ubuntu.com:80 (91.189.88.40). - connect (110: Connection timed out) [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN       
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release.gpg
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick Release       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources     
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.169 80]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe Sources
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/main i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/restricted i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/universe i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.ubuntu.com:80 (91.189.92.169). - connect (110: Connection timed out) [IP: 91.189.92.169 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (91.189.88.40). - connect (110: Connection timed out) [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/i18n/Translation-en_IN.bz2)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to archive.canonical.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_IN.bz2](http://archive.canonical.com/ubuntu/dists/maverick/partner/i18n/Translation-en_IN.bz2)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Could not connect to extras.ubuntu.com:80 (91.189.88.33). - connect (110: Connection timed out)

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2](http://extras.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IN.bz2)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (91.189.92.167). - connect (110: Connection timed out) [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/i18n/Translation-en_IN.bz2)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/source/Sources.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/maverick/partner/binary-i386/Packages.gz)  Unable to connect to archive.canonical.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.167 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.169 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://in.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to in.archive.ubuntu.com:http: [IP: 91.189.88.40 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
```


Please  Help  :confused:

---

### Post by Rubi1200 on 2011-07-06
Hi and welcome to the forums :-)

Try changing to the Main Server and then updating again:

**Ubuntu Software Tab**

 
[LIST]
[*][IMG]https://help.ubuntu.com/community/Repositories/Ubuntu?action=AttachFile&do=get&target=SoftwareSources-UbuntuSoftware.png[/IMG]
[/LIST]

---

### Post by mayurg on 2011-07-07
Hey ! Thanks for the help. I tried but still it couldn't be updated. A pop up window in the end says "Could not download all the repository indexes". When I clicked on details while it was running, it showed failed for each package.

Please Help !!! 

:confused:

:mad:

---

### Post by mayurg on 2011-07-07
Also when I even check for " select best server" in the "others" option in the drop down menu that contains the "Main Server" that you showed, it checks and then in the end it says "cant find a suitable server" and asks to "check your internet connection". But my internet connection is all fine and I am even using internet via Mozilla Firefox.

---

### Post by Rubi1200 on 2011-07-08
Sorry for the delayed response, been busy at work.

Okay, let's try something else to try and troubleshoot this.

Open a terminal and post the output of the following commands:

```
cat /etc/apt/sources.list

ifconfig

cat /etc/hosts
```

After you have pasted the content in a new post, highlight the text and click on the # icon on the menu to wrap the text with code tags. 

It makes it easier to read the content that way.

Thanks.

---

### Post by mayurg on 2011-07-08
Hey Thanks!

Should I enter the code one line after the other or there is some way to put a "enter" or a new line character after every line as in the usual C/C++ or should I just enter them one by one and execute them. Coz whenever I press enter the command gets executed before I can enter the next line of the code you gave me.

PS: I am sorry for my "Dumminess", but I will catch up fast.

:)

---

### Post by mayurg on 2011-07-08
To add to the problems, it is also not hibernating. There is some problem when I try to hibernate.
:(

---

### Post by Rubi1200 on 2011-07-08
Just run each command separately and post the output from each one.

Hibernation: do you have a swap partition and is it activated?

---

### Post by mayurg on 2011-07-08
```
mayur@mayur-Studio-1555:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security multiverse
```

---

### Post by mayurg on 2011-07-08
```
mayur@mayur-Studio-1555:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:09:2b:ca  
          inet addr:10.66.27.22  Bcast:10.66.27.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:fe09:2bca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6020 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2265461 (2.2 MB)  TX bytes:601615 (601.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:d6:26:5e:d4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by mayurg on 2011-07-08
mayur@mayur-Studio-1555:~$ cat /etc/hosts
10.66.27.22    mayur-Studio-1555    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    mayur-Studio-1555    localhost6.localdomain6    localhost6
127.0.1.1    mayur-Studio-1555

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by mayurg on 2011-07-08
Regarding Hibernation, I don't think I made a SWAP partition.

---

### Post by mayurg on 2011-07-08
for hibernation: yes i had made a SWAP partition, but I dont know if its active or not. I dont know how to check...

---

### Post by dino99 on 2011-07-08
start gparted to check the partitions, the swap might be about 4 or 5 Gb to let your system hibernate or/and suspend.

---

### Post by Rubi1200 on 2011-07-08
Regarding swap, what does this command show?

```
free -m
```

Are you behind a proxy or a firewall? Was a setting changed recently that caused the updating issues?

---

### Post by mayurg on 2011-07-09
mayur@mayur-Studio-1555:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2989        432       2556          0         31        202
-/+ buffers/cache:        198       2790
Swap:          192          0        192


Please help for updates. It is of greater importance right now.

---

### Post by Rubi1200 on 2011-07-09
There seems to be one particular link which is broken.

Let's try this in a terminal to try and fix this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command will purge any corrupted sources and the second will refresh them again.

---

### Post by mayurg on 2011-07-10
i tried the code. following is the result:


```
mayur@mayur-Studio-1555:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en                                                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN                                                          
Get:2 [http://archive.canonical.com](http://archive.canonical.com) maverick Release.gpg [198B]                                                                 
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg [72B]                                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en    
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en_IN 
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release [9,762B]             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_IN                                                                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en                                                                                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN                                                                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en                                                                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN                                                                                      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release.gpg [198B]                                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en                                                                                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN                                                                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en                                                                                      
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main Sources [1,073B]                                                                                                          
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main i386 Packages [1,216B]                                                                                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_IN                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en                                                                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en                                                                                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN                                                                                     
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg [198B]                                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en                                                                                            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_IN                                                                                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en                                                                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_IN                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en                                                                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_IN                                                                                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en                                                                                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_IN                                                                                     
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release.gpg [198B]                                                                                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en                                                                                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/main Translation-en_IN                                                                                        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en                                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/multiverse Translation-en_IN                                                                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en                                                                                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/restricted Translation-en_IN                                                                                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en                                                                                       
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-backports/universe Translation-en_IN
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]                                                                                                     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner Translation-en_IN                                                                                            
Get:13 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                                                                                                          
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [31.4kB]                                                                                                    
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release [31.4kB]                                                                                                    
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release [31.4kB]                                                                                                    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports Release [27.2kB]                                                                                                   
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources [829kB]                                                                                                         
Get:19 [http://archive.canonical.com](http://archive.canonical.com) maverick Release [5,925B]                                                                                                          
Get:20 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner Sources [3,994B]                                                                                                  
Get:21 [http://archive.canonical.com](http://archive.canonical.com) maverick/partner i386 Packages [7,774B]                                                                                            
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]                                                                                                  
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse Sources [151kB]                                                                                                   
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe Sources [4,179kB]                                                                                                   
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]                                                                                                 
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]                                                                                                 
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]                                                                                            
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]                                                                                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                                                                                                          
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources [778B]                                                                                            
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [135kB]                                                                                                 
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [135kB]                                                                                                 
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse Sources [2,506B]                                                                                          
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe Sources [46.3kB]                                                                                            
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [375kB]                                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages                                                                                                      
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages [152kB]
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,206B]                                                                                    
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted Sources [14B]                                                                                            
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main Sources [44.6kB]                                                                                               
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse Sources [1,758B]                                                                                         
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe Sources [18.8kB]                                                                                           
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages [153kB]                                                                                          
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/main i386 Packages [153kB]                                                                                          
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/restricted i386 Packages [14B]                                                                                      
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/universe i386 Packages [73.0kB]                                                                                     
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security/multiverse i386 Packages [3,746B]                                                                                   
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]                                                                                      
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages [123kB]
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]                                                                                   
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages [10.6kB]                                                                                     
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/restricted i386 Packages [14B]                                                                                     
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/main i386 Packages [10.5kB]                                                                                        
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/multiverse i386 Packages [14B]                                                                                     
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-backports/universe i386 Packages [12.7kB]                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages                                                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages                                                                                                      
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [7,480kB]                                                                                             
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [487kB]                                                                                           
Fetched 4,737kB in 3h 47min 21s (347B/s)                                                                                                                               
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.
mayur@mayur-Studio-1555:~$
```

---

### Post by Rubi1200 on 2011-07-10
I don't understand this, I can download those packages by clicking on the link.

Try this:

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

---

