---
title: "Update (sudo apt update) errors ??"
date: 2021-07-22
forum: Installation &amp; Upgrades
---

### Post by oygle on 2021-07-22
```
$ sudo apt update
```

> [sudo] password for ******: 
Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease                                                                  
Get:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]                                                     
Hit:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                                     
Hit:6 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal InRelease       
Get:7 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1,126 kB]
Get:8 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [511 kB]                                                  
Get:9 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main Translation-en [245 kB]                                                 
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]                                         
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]                                         
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]                                         
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]                                         
Ign:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata                                                  
Ign:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata                                              
Ign:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata                                            
Get:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]                                         
Err:10 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata                                                  
  File has unexpected size (282604 != 282768). Mirror sync in progress? [IP: 202.158.214.106 80]
  Hashes of expected file:
   - Filesize:282768 [weak]
   - SHA256:c231da4bc2d54ee9a97ccfd45a7625b66194c4f9eb5a6db44ac700fc21b8f10e
   - SHA1:8c479b82f9496eab448a023d1c84b5507c0f89e4 [weak]
   - MD5Sum:580ed4282658fb870ae13a6f96b29c19 [weak]
  Release file created at: Thu, 22 Jul 2021 20:25:59 +0000
Get:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [339 kB]                                     
Err:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata                                        
  
Hit:17 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) focal InRelease                                                                     
Get:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]                                  
Err:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata          
  
Ign:4 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 InRelease                                          
Hit:18 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 Release
Fetched 116 kB in 2s (53.0 kB/s)
Reading package lists... Done
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz](http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/main/dep11/Components-amd64.yml.xz)  File has unexpected size (282604 != 282768). Mirror sync in progress? [IP: 202.158.214.106 80]
   Hashes of expected file:
    - Filesize:282768 [weak]
    - SHA256:c231da4bc2d54ee9a97ccfd45a7625b66194c4f9eb5a6db44ac700fc21b8f10e
    - SHA1:8c479b82f9496eab448a023d1c84b5507c0f89e4 [weak]
    - MD5Sum:580ed4282658fb870ae13a6f96b29c19 [weak]
   Release file created at: Thu, 22 Jul 2021 20:25:59 +0000
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz](http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/universe/dep11/Components-amd64.yml.xz)  
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz](http://au.archive.ubuntu.com/ubuntu/dists/focal-updates/multiverse/dep11/Components-amd64.yml.xz)  
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by MAFoElffen on 2021-07-22
Wait a little bit and try again... It told you it was in the middle of a mirror sync... It will resolve itself in due time.

---

### Post by oygle on 2021-07-22
> **MAFoElffen said:**
> Wait a little bit and try again... It told you it was in the middle of a mirror sync... It will resolve itself in due time.

Thanks, as you say, it's okay now.

---

