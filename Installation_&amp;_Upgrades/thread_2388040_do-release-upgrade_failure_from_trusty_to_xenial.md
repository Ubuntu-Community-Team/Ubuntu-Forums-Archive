---
title: "do-release-upgrade failure from trusty to xenial"
date: 2018-03-27
forum: Installation &amp; Upgrades
---

### Post by wmjosiah on 2018-03-27
Hi all,

I have a fully updated 14.0.4.5 LTS server box that I'm trying to upgrade to 16.0.4 with do-release-upgrade. I get:

```
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [836 B]                                                                               
Get:2 Upgrade tool [1,249 kB]                                                                                      
Fetched 1,250 kB in 0s (0 B/s)                                                                                     
authenticate 'xenial.tar.gz' against 'xenial.tar.gz.gpg' 
gpg exited 1
```
Debug information: 
```
gpg: Signature made Thu 26 Jan 2017 12:36:10 PM EST using RSA key ID C0B21F32
gpg: /tmp/ubuntu-release-upgrader-zhgllyaf/trustdb.gpg: trustdb created
gpg: BAD signature from "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>"

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 
```
Should I be worried that I've been compromised? I've done the following, and apt-get update completes without error, as do dist-upgrades, which I do very regularly.
```
sudo apt-key update
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
```
Any advice or next steps? Thanks in advance. There are no proxies on my network.

---

### Post by wmjosiah on 2018-03-28
I just tried this same thing on another Ubuntu 14.0.4 box of mine and got the same result. I see other posts around about this about changing your apt sources, so I've tried using both "archive.ubuntu.com" and "us.archive.ubuntu.com". Here's the output of my apt-get update - anyone see anything wrong?
```
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
```

---

### Post by Frogs Hair on 2018-03-28
Hello and Welcome !

Please use code tags for terminal outputs. Highlight the pasted text with the the cursor and select the # symbol from the reply box tools.

---

### Post by wmjosiah on 2018-03-29
Will do. Also, the solution to my problem is embarrassing. There actually was a proxy config that I wasn't aware of in /etc/apt/apt.conf.d/01proxy that had been put there by puppet, so the answer to my initial question is that I was wrong :) Removing the proxy config solved the problem.

---

