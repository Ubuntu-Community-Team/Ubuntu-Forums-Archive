---
title: "problem updating"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by oho27m on 2015-12-17
Hi, 

I have a problem with apt-get update.
I guess you need to edit /etc/apt/sources.list but I don't know what to insert

This is the output command


```
root@ubuntuIT:/home/ubuntuIT# apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages        
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages      
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages             
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages       
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en
  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en_US](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en_US)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en](http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en)  Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:67c:1562::17). - connect (101: Network is unreachable) [IP: 2001:67c:1562::17 80]


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bucky Ball on 2015-12-17
Is there any reason you're running in the terminal as root? Best to avoid unless required. Simply use:

```
sudo apt-get update
```

... etc., as a regular user. 

Have you tried changing the mirror in 'Software and Updates'?

PS: See link in my signature for code tags. :)

---

### Post by oho27m on 2015-12-18
thanks for the reply.

Yes, I tried as root but it's the same.

---

### Post by oho27m on 2015-12-18
I edit file [COLOR=#000000]/etc/apt/sources.list .
now I use [/COLOR]http://archive.ubuntu.com/ubuntu/ for update and it's work.

---

### Post by Bucky Ball on 2015-12-20
Great news. Have been away for awhile so glad to see it's working. If you're happy, please see the first link in my signature and good luck. :)

---

