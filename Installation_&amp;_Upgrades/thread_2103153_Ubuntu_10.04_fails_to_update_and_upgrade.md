---
title: "Ubuntu 10.04 fails to update and upgrade"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by lucaghera on 2013-01-09
I have a problem with a pc running Ubuntu 10.04

Each time I try to *sudo apt-get update* it stops to download after few time:

```
Get:1 http://it.archive.ubuntu.com precise Release.gpg [198B]                  
Ign http://it.archive.ubuntu.com/ubuntu/ precise/main Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise/restricted Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise/universe Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise/multiverse Translation-en_US
Get:2 http://it.archive.ubuntu.com precise-updates Release.gpg [198B]
Ign http://it.archive.ubuntu.com/ubuntu/ precise-updates/main Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise-updates/restricted Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise-updates/universe Translation-en_US
Get:3 http://security.ubuntu.com precise-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ precise-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ precise-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ precise-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ precise-security/multiverse Translation-en_US
Ign http://it.archive.ubuntu.com/ubuntu/ precise-updates/multiverse Translation-en_US
Get:4 http://it.archive.ubuntu.com precise Release [49.6kB]
Get:5 http://security.ubuntu.com precise-security Release [49.6kB]
Get:6 http://it.archive.ubuntu.com precise-updates Release [49.6kB]
Get:7 http://security.ubuntu.com precise-security/main Packages [221kB]        
Get:8 http://it.archive.ubuntu.com precise/main Packages [1,274kB]
Get:9 http://security.ubuntu.com precise-security/restricted Packages [3,968B] 
Get:10 http://security.ubuntu.com precise-security/main Sources [59.6kB]       
Get:11 http://it.archive.ubuntu.com precise/main Packages [1,274kB]            
Get:12 http://security.ubuntu.com precise-security/restricted Sources [1,950B] 
Get:13 http://security.ubuntu.com precise-security/universe Packages [61.1kB]  
Get:14 http://security.ubuntu.com precise-security/universe Sources [18.9kB]   
Get:15 http://it.archive.ubuntu.com precise/main Packages [1,274kB]
Get:16 http://it.archive.ubuntu.com precise/main Packages [1,274kB]
41% [16 Packages 243kB/1,274kB 19%] [14 Sources 2,497B/18.9kB 13%]
```In the same way if I try to upgrade to 12.04 it stocks during the first step and if I cancel the operation it returns the following errors:

```
W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise/main/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise/restricted/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise/universe/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise/multiverse/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise-updates/main/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://it.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/main/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/restricted/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/universe/i18n/Translation-en_US.bz2  
, W:Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/multiverse/i18n/Translation-en_US.bz2  
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```How can I fix it?

Thanks in advance,
Luca

---

### Post by Rebelli0us on 2013-01-09
I think 10.04 and 10.10 are outdated. Why not use a newer distro?

---

