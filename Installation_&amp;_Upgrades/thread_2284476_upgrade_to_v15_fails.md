---
title: "upgrade to v15 fails"
date: 2015-06-29
forum: Installation &amp; Upgrades
---

### Post by Gary_Hobbs on 2015-06-29
I have been trying to upgrade from 14.10 to 15 using the update manager and it always fails on getting new packages.

I'm using the usa server.  I can ping the IP of the server it listed. 
the message stated the the connection timed out and then ended the upgrade.

I have tried multiple servers with the same result.  Could our firewall be blocking the packages??

I tried using command line and get these errors:

   Fetching
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-headers-3.19.0-21 all 3.19.0-21.21
  Connection failed [IP: 91.189.91.23 80]                                      
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-security/main linux-headers-3.19.0-21 all 3.19.0-21.21 [9,331 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-security/main linux-headers-3.19.0-21 all 3.19.0-21.21 [9,331 kB]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-security/main linux-headers-3.19.0-21 all 3.19.0-21.21
  Connection failed [IP: 91.189.91.13 80]                                      
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-updates/main linux-headers-3.19.0-21 all 3.19.0-21.21
  Connection failed [IP: 91.189.91.24 80]                

upgrade never finishes.

---

### Post by dino99 on 2015-06-30
instead of the local mirror, switch to the 'main' server to test again. But be sure to have a cleaned /etc/apt/sources.list: no third party source, no active ppa; then do > rm /var/cache/apt/archives/*

---

### Post by Gary_Hobbs on 2015-06-30
I had issues in clearing the sources.list.  I gave up and installed a clean version of vivid.

---

