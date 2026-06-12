---
title: "After 6months on no use, errors during update"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by bizres on 2018-05-08
Hello,

I've not used my Ubuntu 17.04 PC for about 6 months now as was on travel, but yesterday logged in and update came up.

Continued with the update but keep geeting the error 
[[img]https://s7.postimg.cc/u0q4rfgkn/Screenshot_from_2018-05-07_23-57-41.png[/img]](https://postimg.cc/image/u0q4rfgkn/)

Results from sudo apt-get update:
```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://archive.canonical.com](http://archive.canonical.com) zesty InRelease                             
Ign:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty InRelease                      
Ign:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Hit:5 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease                              
Ign:6 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-backports InRelease            
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Ign:8 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security InRelease             
Hit:10 [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) zesty InRelease
Err:11 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty Release                       
  404  Not Found [IP: 91.189.88.162 80]
Hit:12 [http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu) zesty InRelease   
Err:13 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-updates Release
  404  Not Found [IP: 91.189.88.162 80]
Err:14 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-backports Release
  404  Not Found [IP: 91.189.88.162 80]
Ign:15 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security Release
Ign:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Ign:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons
Ign:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 Packages
Ign:29 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all Packages
Ign:30 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted i386 Packages
Ign:31 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en_CA
Ign:32 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en
Ign:33 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all DEP-11 Metadata
Ign:34 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 DEP-11 Metadata
Ign:35 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted DEP-11 64x64 Icons
Ign:36 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe i386 Packages
Ign:37 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
Ign:38 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all Packages
Ign:39 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en_CA
Ign:40 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en
Ign:41 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all DEP-11 Metadata
Ign:42 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata
Ign:43 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons
Ign:44 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all Packages
Ign:45 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse i386 Packages
Ign:46 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 Packages
Ign:47 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en
Ign:48 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en_CA
Ign:49 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata
Ign:50 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all DEP-11 Metadata
Ign:51 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse DEP-11 64x64 Icons
Ign:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Ign:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons
Ign:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 Packages
Ign:29 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all Packages
Ign:30 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted i386 Packages
Ign:31 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en_CA
Ign:32 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en
Ign:33 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all DEP-11 Metadata
Ign:34 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 DEP-11 Metadata
Ign:35 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted DEP-11 64x64 Icons
Ign:36 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe i386 Packages
Ign:37 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
Ign:38 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all Packages
Ign:39 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en_CA
Ign:40 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en
Ign:41 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all DEP-11 Metadata
Ign:42 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata
Ign:43 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons
Ign:44 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all Packages
Ign:45 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse i386 Packages
Ign:46 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 Packages
Ign:47 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en
Ign:48 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en_CA
Ign:49 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata
Ign:50 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all DEP-11 Metadata
Ign:51 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse DEP-11 64x64 Icons
Ign:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Ign:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons
Ign:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 Packages
Ign:29 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all Packages
Ign:30 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted i386 Packages
Ign:31 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en_CA
Ign:32 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en
Ign:33 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all DEP-11 Metadata
Ign:34 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 DEP-11 Metadata
Ign:35 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted DEP-11 64x64 Icons
Ign:36 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe i386 Packages
Ign:37 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
Ign:38 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all Packages
Ign:39 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en_CA
Ign:40 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en
Ign:41 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all DEP-11 Metadata
Ign:42 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata
Ign:43 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons
Ign:44 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all Packages
Ign:45 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse i386 Packages
Ign:46 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 Packages
Ign:47 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en
Ign:48 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en_CA
Ign:49 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata
Ign:50 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all DEP-11 Metadata
Ign:51 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse DEP-11 64x64 Icons
Ign:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Ign:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons
Ign:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 Packages
Ign:29 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all Packages
Ign:30 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted i386 Packages
Ign:31 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en_CA
Ign:32 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en
Ign:33 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all DEP-11 Metadata
Ign:34 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 DEP-11 Metadata
Ign:35 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted DEP-11 64x64 Icons
Ign:36 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe i386 Packages
Ign:37 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
Ign:38 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all Packages
Ign:39 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en_CA
Ign:40 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en
Ign:41 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all DEP-11 Metadata
Ign:42 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata
Ign:43 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons
Ign:44 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all Packages
Ign:45 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse i386 Packages
Ign:46 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 Packages
Ign:47 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en
Ign:48 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en_CA
Ign:49 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata
Ign:50 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all DEP-11 Metadata
Ign:51 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse DEP-11 64x64 Icons
Ign:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Ign:27 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main DEP-11 64x64 Icons
Ign:28 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 Packages
Ign:29 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all Packages
Ign:30 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted i386 Packages
Ign:31 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en_CA
Ign:32 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Translation-en
Ign:33 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted all DEP-11 Metadata
Ign:34 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted amd64 DEP-11 Metadata
Ign:35 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted DEP-11 64x64 Icons
Ign:36 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe i386 Packages
Ign:37 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 Packages
Ign:38 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all Packages
Ign:39 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en_CA
Ign:40 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Translation-en
Ign:41 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe all DEP-11 Metadata
Ign:42 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe amd64 DEP-11 Metadata
Ign:43 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe DEP-11 64x64 Icons
Ign:44 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all Packages
Ign:45 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse i386 Packages
Ign:46 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 Packages
Ign:47 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en
Ign:48 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Translation-en_CA
Ign:49 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse amd64 DEP-11 Metadata
Ign:50 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse all DEP-11 Metadata
Ign:51 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse DEP-11 64x64 Icons
Err:16 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/multiverse Sources
  404  Not Found [IP: 91.189.88.162 80]
Ign:17 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Sources
Ign:18 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/universe Sources
Ign:19 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/restricted Sources
Ign:20 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main i386 Packages
Ign:21 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 Packages
Ign:22 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all Packages
Ign:23 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en
Ign:24 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main Translation-en_CA
Ign:25 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main all DEP-11 Metadata
Ign:26 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) zesty-security/main amd64 DEP-11 Metadata
Reading package lists... Done
E: The repository 'http://ca.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ca.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ca.archive.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Tried to upgrade from Synaptic and get the error:
```
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libseccomp/libseccomp2_2.3.1-2.1ubuntu2~17.04.1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/libs/libseccomp/libseccomp2_2.3.1-2.1ubuntu2~17.04.1_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu1.2_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu1.2_all.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-plugin-snap_3.22.7-0ubuntu3.17.04.7_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-plugin-snap_3.22.7-0ubuntu3.17.04.7_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.22.7-0ubuntu3.17.04.7_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software_3.22.7-0ubuntu3.17.04.7_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.22.7-0ubuntu3.17.04.7_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/gnome-software-common_3.22.7-0ubuntu3.17.04.7_all.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xen/libxenstore3.0_4.8.0-1ubuntu2.4_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xen/libxenstore3.0_4.8.0-1ubuntu2.4_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xen/libxen-4.8_4.8.0-1ubuntu2.4_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xen/libxen-4.8_4.8.0-1ubuntu2.4_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.22.7-0ubuntu3.17.04.7_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gnome-software/ubuntu-software_3.22.7-0ubuntu3.17.04.7_all.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/w/wpa/wpasupplicant_2.4-0ubuntu9.1_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/w/wpa/wpasupplicant_2.4-0ubuntu9.1_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.19.3-1ubuntu1.3_all.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.19.3-1ubuntu1.3_all.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xmir_1.19.3-1ubuntu1.3_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xmir_1.19.3-1ubuntu1.3_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]


W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.19.3-1ubuntu1.3_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.19.3-1ubuntu1.3_amd64.deb)
  404  Not Found [IP: 91.189.88.162 80]
```

Would really appreciate some help on this, pls.

---

### Post by wildmanne39 on 2018-05-08
That is because 17.04 is no longer supported, I recommend you back up your important data and do a fresh install of 18.04 because you will not be able to easily upgrade 17.04 since it is no longer supported and it is not worth the time and trouble it will take to try to do an upgrade.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by QIII on 2018-05-08
Hello!

Please use code tags for terminal commands and results.  You may do so with the # button in the toolbars above the text entry box.

17.04 has passed its End Of Life (EOL) and is no longer supported and the repositories have been moved.  I would suggest installing a currently supported release.  You can find out which releases are supported and which have passed EOL [here]("https://wiki.ubuntu.com/Releases").

If you are unsure how to do a fresh install while preserving your important files, please let us know.

---

