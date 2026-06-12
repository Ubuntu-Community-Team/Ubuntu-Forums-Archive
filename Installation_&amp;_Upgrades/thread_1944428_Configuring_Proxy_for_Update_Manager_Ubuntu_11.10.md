---
title: "Configuring Proxy for Update Manager Ubuntu 11.10"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by fredwhite on 2012-03-21
Hi,

I am at college and i have connect to the Internet through a proxy. Because of this i am unable to run update manager or update using apt-get update. 

I have tried various fixes like editing the bash file, apt.conf bu nothing seems to work. I have also applied system wide settings through the network gui. But nothing seems to really work. I really need ubuntu software center to run as i have to install media plugins, vlc etc. 

When i run update manager, i get the error Failed to download Repository Information, Check your internet. 

[B]sudo apt-get error
[/B]
 ater@ater:~$ sudo apt-get update
[sudo] password for ater: 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric InRelease                  
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release.gpg                           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release.gpg                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release.gpg                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release                     
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                       
  403  Forbidden
Err [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
  403  Forbidden
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main TranslationIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe TranslationIndex             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages 
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources                          
  403  Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources                    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources                      
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages              
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages                
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages              
  403  Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Sources            
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Sources              
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  403  Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Sources    
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Sources
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe i386 Packages
  403  Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
  403  Forbidden
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en_IN                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en_IN
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en_IN  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources)  403  Forbidden

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages](http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  403  Forbidden

W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  403  Forbidden

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by cortman on 2012-03-21
Hi fredwhite, welcome to the Forums!

Could your problem be resolved by going to Settings>Network>Proxy and changing it there?

EDIT: Only now realized you tried that already. Are you sure you got the proxy address, ports, etc. correct? I assume it's probably an http(s) proxy, which uses ports 80 and 8080.
You might confirm by copying the proxy address that you typed into the network GUI and pinging it.

---

