---
title: "Unable to update using terminal or update manager"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by LilProfess on 2010-12-24
Ok every time i try to update my computer i get this message
administrator@desktop:~$ sudo aptitude upgrade 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

administrator@desktop:~$ sudo apt-get install --fix-broken
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
administrator@desktop:~$ 


Along with when i use the update manager
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to 192.168.1.2:3142 (192.168.1.2). - connect (110: Connection timed out)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  Unable to connect to 192.168.1.2:3142:
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to 192.168.1.2:3142:
Some index files failed to download, they have been ignored, or old ones used instead.

Any suggestions?

---

### Post by Rubi1200 on 2010-12-26
Hi and welcome to the forums :)

So, did you try the safe-upgrade option?

What does ```
sudo dpkg --configure -a
``` tell you?

---

### Post by LilProfess on 2010-12-26
administrator@desktop:~$ sudo dpkg --configure -a
[sudo] password for administrator: 

That's all every time it just says
administrator@desktop:~$ sudo dpkg --configure -a
then skips to the next line

---

### Post by karthick87 on 2010-12-26
Did you run update after executing,
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by kiran r on 2010-12-26
sudo apt-get update  will probably solve ur problem

---

### Post by LilProfess on 2010-12-26
administrator@desktop:~$ sudo dpkg --configure -a
[sudo] password for administrator: 
administrator@desktop:~$ sudo aptitude update
0% [Waiting for headers]sudo aptitude upgrade 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]                  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                             
  
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [38.5kB]                 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                            
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources                          
Fetched 587B in 20s (29B/s)                                                     
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5


administrator@desktop:~$ sudo aptitude upgrade 
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

administrator@desktop:~$

---

### Post by LilProfess on 2010-12-26
administrator@desktop:~$ sudo dpkg --configure -a
administrator@desktop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release    
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
  
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [38.5kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Fetched 587B in 2min 5s (5B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
administrator@desktop:~$

---

### Post by karthick87 on 2010-12-26
Try,
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
```
```
sudo apt-get update
```

---

### Post by LilProfess on 2010-12-28
Ok so this is what it said on my Terminal

administrator@desktop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
[sudo] password for administrator: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
administrator@desktop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [38.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [375kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]     
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [141kB]             
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]      
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [158kB]       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [61.4kB]       
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [7,366B]    
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [3,677B]     
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [114kB]          
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]      
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources [38.2kB]          
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [14B]       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [53.4kB]     
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources [15.3kB]      
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [2,003B]   
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources [660B]      
Fetched 975kB in 2min 45s (5,902B/s)                                           
Reading package lists... Done
administrator@desktop:~$ 


And then my update manager said when i tried to update
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_7.4-2ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/coreutils/coreutils_7.4-2ubuntu3_i386.deb)
  Could not connect to 192.168.1.2:3142 (192.168.1.2). - connect (110: Connection timed out)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-bin_2.11.1-0ubuntu7.6_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6_2.11.1-0ubuntu7.6_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i686_2.11.1-0ubuntu7.6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i686_2.11.1-0ubuntu7.6_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7.6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc-dev-bin_2.11.1-0ubuntu7.6_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.6_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-dev_2.11.1-0ubuntu7.6_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-27.49_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-27.49_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010o-0ubuntu0.10.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2010o-0ubuntu0.10.04_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/libdevmapper1.02.1_1.02.39-1ubuntu4.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98-1ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.98-1ubuntu9_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.11-1ubuntu2.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.11-1ubuntu2.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.98-1ubuntu9_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.15.5.6ubuntu4.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.41.11-1ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.41.11-1ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.12-9ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.12-9ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.22-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tar/tar_1.22-2ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.41.11-1ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.8.1+dfsg-2ubuntu0.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8k-7ubuntu8.5_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.10.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_3.10.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.10.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_3.10.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.10.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/libhpmud0_3.10.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.7-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python-imaging/python-imaging_1.1.7-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.21-0ubuntu5.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openldap/libldap-2.4-2_2.4.21-0ubuntu5.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler5_0.12.4-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler5_0.12.4-0ubuntu5.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.12.4-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.12.4-0ubuntu5.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.71.dfsg.1-0ubuntu5.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.71.dfsg.1-0ubuntu5.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.71.dfsg.1-0ubuntu5.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.71.dfsg.1-0ubuntu5.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.3-1ubuntu1.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.3-1ubuntu1.3_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/update-inetd/update-inetd_4.35ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-inetd/update-inetd_4.35ubuntu0.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.3-1ubuntu1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.3-1ubuntu1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.2-2ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_3.10.2-2ubuntu2.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_10.04+20100714_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_10.04+20100714_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_10.04+20100714_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_10.04+20100714_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_10.04+20100714_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_10.04+20100714_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_10.04+20100714_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_10.04+20100714_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-24-generic_2.6.32-24.43_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-27-generic_2.6.32-27.49_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-27-generic_2.6.32-27.49_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.25.3ubuntu9.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.41.11-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.41.11-1ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.25.3ubuntu9.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.5-4ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.5-4ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.5-4ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_151-12.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_151-12.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.28.0-0ubuntu2.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.28.0-0ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-label_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-label_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/ifupdown/ifupdown_0.6.8ubuntu29.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_151-12.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_151-12.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lvm2/dmsetup_1.02.39-1ubuntu4.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-x11_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-x11_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/libplymouth2_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/libplymouth2_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mountall/mountall_2.15.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.6.5-7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.6.5-7_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/r/rsyslog/rsyslog_4.2.0-2ubuntu8.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rsyslog/rsyslog_4.2.0-2ubuntu8.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-4.1.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.100.0-4.1.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.12-1.1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.12-1.1ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.5.1-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.5.1-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.5.1-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.5.1-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.5.1-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.5.1-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-transport-https_0.7.25.3ubuntu9.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns64_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-60_9.7.0.dfsg.P1-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/man-db/man-db_2.5.7-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/man-db/man-db_2.5.7-2ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-text_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.134.11_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.134.11_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.11_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.134.11_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.10.04.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.10.04.4_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core6_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core6_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-utils_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20.1-3ubuntu7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20.1-3ubuntu7_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_1.2.1-0ubuntu1.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-common_1.2.1-0ubuntu1.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_1.2.1-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter-bdb_1.2.1-0ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_1.2.1-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bogofilter/bogofilter_1.2.1-0ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/libgutenprint2_5.2.5-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/libgutenprint2_5.2.5-0ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_8.71.dfsg.1-0ubuntu5.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-cups_8.71.dfsg.1-0ubuntu5.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/cups-driver-gutenprint_5.2.5-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gutenprint/cups-driver-gutenprint_5.2.5-0ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/python-avahi_0.6.25-1ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/python-avahi_0.6.25-1ubuntu6.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/python-desktopcouch_0.6.4-0ubuntu3.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/python-desktopcouch_0.6.4-0ubuntu3.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/python-desktopcouch-records_0.6.4-0ubuntu3.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/python-desktopcouch-records_0.6.4-0ubuntu3.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/desktopcouch_0.6.4-0ubuntu3.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/desktopcouch/desktopcouch_0.6.4-0ubuntu3.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/dnsmasq/dnsmasq-base_2.52-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/dnsmasq/dnsmasq-base_2.52-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.5-0ubuntu0.10.04.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-common_1.2.5-0ubuntu0.10.04.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/w/webkit/libwebkit-1.0-2_1.2.5-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_2.30.3-0ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.30.3-0ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-common_2.30.3-0ubuntu1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-xmerl_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-xmerl_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-syntax-tools_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-syntax-tools_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-inets_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-inets_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-mnesia_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-mnesia_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-runtime-tools_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-runtime-tools_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-ssl_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-ssl_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-public-key_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-public-key_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-crypto_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-crypto_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-base_13.b.3-dfsg-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/erlang/erlang-base_13.b.3-dfsg-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.10.04.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.8.6-0ubuntu0.10.04.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.8-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.102.65ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.102.65ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.102.65ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.102.65ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi_0.6.0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi_0.6.0ubuntu2_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-core_0.6.0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdebi/gdebi-core_0.6.0ubuntu2_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.71.dfsg.1-0ubuntu5.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.71.dfsg.1-0ubuntu5.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.30.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.30.2-0ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.30.2-0ubuntu1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mako/python-mako_0.2.5-2ubuntu1.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mako/python-mako_0.2.5-2ubuntu1.3_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.30.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber_2.30.3-0ubuntu1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.30.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gwibber/gwibber-service_2.30.3-0ubuntu1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2_6.5.7.8-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2_6.5.7.8-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand2_6.5.7.8-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand2_6.5.7.8-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.5.7.8-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/imagemagick_6.5.7.8-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_4.0.2-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lftp/lftp_4.0.2-1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu6.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/couchdb-glib/libcouchdb-glib-1.0-2_0.6.3-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/couchdb-glib/libcouchdb-glib-1.0-2_0.6.3-0ubuntu2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/couchdb-glib/libdesktopcouch-glib-1.0-2_0.6.3-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/couchdb-glib/libdesktopcouch-glib-1.0-2_0.6.3-0ubuntu2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/djvulibre/libdjvulibre-text_3.5.22-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/djvulibre/libdjvulibre-text_3.5.22-1ubuntu4.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/djvulibre/libdjvulibre21_3.5.22-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/djvulibre/libdjvulibre21_3.5.22-1ubuntu4.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgdiplus/libgdiplus_2.4.2-1ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgdiplus/libgdiplus_2.4.2-1ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgksu/libgksu2-0_2.0.13~pre1-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgksu/libgksu2-0_2.0.13~pre1-1ubuntu4.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_151-12.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_151-12.3_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea5_2009-5ubuntu0.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea5_2009-5ubuntu0.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2-extra_6.5.7.8-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore2-extra_6.5.7.8-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmikmod/libmikmod2_3.1.11-a-6.1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libm/libmikmod/libmikmod2_3.1.11-a-6.1ubuntu0.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.4-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.4-0ubuntu5.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.6.6-1ubuntu4.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.6.6-1ubuntu4.2_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.6-1ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.6-1ubuntu4.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.6.2-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.6.2-0ubuntu5.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.6.2-0ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.6.2-0ubuntu5.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.7~dfsg-1ubuntu3.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libw/libwww-perl/libwww-perl_5.834-1ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libw/libwww-perl/libwww-perl_5.834-1ubuntu0.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.6.dfsg-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.6.dfsg-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.27.29_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.27.29_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.27.29_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.27.29_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24_2.6.32-24.43_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-24-generic_2.6.32-24.43_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-27_2.6.32-27.49_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-27_2.6.32-27.49_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-27-generic_2.6.32-27.49_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-27-generic_2.6.32-27.49_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.27.29_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.27.29_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8k-7ubuntu8.5_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.2-2ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/plymouth/plymouth-theme-ubuntu-logo_0.8.2-2ubuntu2.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.9.11-1ubuntu1.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lazr.restfulclient/python-lazr.restfulclient_0.9.11-1ubuntu1.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.6.dfsg-1ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.4.8-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/papyon/python-papyon_0.4.8-0ubuntu2_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/software-properties/python-software-properties_0.75.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/software-properties/python-software-properties_0.75.10.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.7~dfsg-1ubuntu3.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.7~dfsg-1ubuntu3.2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.7~dfsg-1ubuntu3.2_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.7~dfsg-1ubuntu3.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.3-14ubuntu1.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/screen/screen_4.0.3-14ubuntu1.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.75.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.75.10.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p1-1ubuntu5.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.7.2p1-1ubuntu5.2_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/thaifonts-scalable/ttf-thai-tlwg_0.4.13-4ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/thaifonts-scalable/ttf-thai-tlwg_0.4.13-4ubuntu0.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.9~rc2-0ubuntu2.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-gtk_0.2.22.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-gtk_0.2.22.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.22.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/usb-creator/usb-creator-common_0.2.22.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.4_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.4_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.13+build3+nobinonly-0ubuntu0.10.04.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.11+bzr345-0ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon-gtk_0.11+bzr345-0ubuntu4.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.11+bzr345-0ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.11+bzr345-0ubuntu4.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.11+bzr345-0ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/python-aptdaemon_0.11+bzr345-0ubuntu4.1_all.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/fglrx-installer/fglrx-modaliases_8.723.1-0ubuntu5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/fglrx-installer/fglrx-modaliases_8.723.1-0ubuntu5_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.30.1-0ubuntu1.1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.2.6-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/indicator-sound/indicator-sound_0.2.6-0ubuntu1_i386.deb)
  Unable to connect to 192.168.1.2:3142:


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20100716-1ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mobile-broadband-provider-info/mobile-broadband-provider-info_20100716-1ubuntu0.1_all.deb)
  Unable to connect to 192.168.1.2:3142:

---

