---
title: "Problem with update."
date: 2016-09-21
forum: Installation &amp; Upgrades
---

### Post by dafhorz on 2016-09-21
Hope you're having a good day and thank you for your support.

The thing is that when I try to upgrade from terminal I got the following:

```

sudo apt-get update
Ign:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Ign:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease
Ign:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease
Ign:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease
Ign:5 http://archive.ubuntu.com/ubuntu xenial Release         
Ign:6 http://archive.ubuntu.com/ubuntu xenial-updates Release 
Ign:7 http://archive.ubuntu.com/ubuntu xenial-backports Release
Ign:8 http://archive.ubuntu.com/ubuntu xenial-security Release
Ign:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Ign:20 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en
Ign:21 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:22 http://archive.ubuntu.com/ubuntu xenial/restricted DEP-11 64x64 Icons
Ign:23 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Ign:24 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
Ign:25 http://archive.ubuntu.com/ubuntu xenial/universe all Packages
Ign:26 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en_US
Ign:27 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en
Ign:28 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:29 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:30 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
Ign:31 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
Ign:32 http://archive.ubuntu.com/ubuntu xenial/multiverse all Packages
Ign:33 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_US
Ign:34 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en
Ign:35 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:36 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons
Ign:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Ign:48 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en
Ign:49 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:50 http://archive.ubuntu.com/ubuntu xenial-updates/restricted DEP-11 64x64 Icons
Ign:51 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Ign:52 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
Ign:53 http://archive.ubuntu.com/ubuntu xenial-updates/universe all Packages
Ign:54 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en_US
Ign:55 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en
Ign:56 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:57 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:58 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
Ign:59 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
Ign:60 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse all Packages
Ign:61 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en_US
Ign:62 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en
Ign:63 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:64 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Ign:76 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en
Ign:77 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:78 http://archive.ubuntu.com/ubuntu xenial-backports/restricted DEP-11 64x64 Icons
Ign:79 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu xenial-backports/universe all Packages
Ign:82 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en_US
Ign:83 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en
Ign:84 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:85 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:86 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages
Ign:87 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages
Ign:88 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse all Packages
Ign:89 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en_US
Ign:90 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en
Ign:91 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:92 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Ign:104 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:105 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted DEP-11 64x64 Icons
Ign:107 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:108 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Ign:109 http://archive.ubuntu.com/ubuntu xenial-security/universe all Packages
Ign:110 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en_US
Ign:111 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en
Ign:112 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:113 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:114 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
Ign:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
Ign:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse all Packages
Ign:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en_US
Ign:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en
Ign:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:120 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Ign:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Ign:20 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en
Ign:21 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:22 http://archive.ubuntu.com/ubuntu xenial/restricted DEP-11 64x64 Icons
Ign:23 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Ign:24 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
Ign:25 http://archive.ubuntu.com/ubuntu xenial/universe all Packages
Ign:26 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en_US
Ign:27 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en
Ign:28 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:29 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:30 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
Ign:31 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
Ign:32 http://archive.ubuntu.com/ubuntu xenial/multiverse all Packages
Ign:33 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_US
Ign:34 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en
Ign:35 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:36 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons
Ign:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Ign:48 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en
Ign:49 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:50 http://archive.ubuntu.com/ubuntu xenial-updates/restricted DEP-11 64x64 Icons
Ign:51 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Ign:52 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
Ign:53 http://archive.ubuntu.com/ubuntu xenial-updates/universe all Packages
Ign:54 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en_US
Ign:55 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en
Ign:56 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:57 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:58 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
Ign:59 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
Ign:60 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse all Packages
Ign:61 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en_US
Ign:62 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en
Ign:63 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:64 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Ign:76 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en
Ign:77 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:78 http://archive.ubuntu.com/ubuntu xenial-backports/restricted DEP-11 64x64 Icons
Ign:79 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu xenial-backports/universe all Packages
Ign:82 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en_US
Ign:83 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en
Ign:84 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:85 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:86 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages
Ign:87 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages
Ign:88 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse all Packages
Ign:89 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en_US
Ign:90 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en
Ign:91 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:92 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Ign:104 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:105 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted DEP-11 64x64 Icons
Ign:107 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:108 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Ign:109 http://archive.ubuntu.com/ubuntu xenial-security/universe all Packages
Ign:110 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en_US
Ign:111 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en
Ign:112 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:113 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:114 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
Ign:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
Ign:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse all Packages
Ign:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en_US
Ign:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en
Ign:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:120 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Ign:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Ign:20 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en
Ign:21 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:22 http://archive.ubuntu.com/ubuntu xenial/restricted DEP-11 64x64 Icons
Ign:23 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Ign:24 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
Ign:25 http://archive.ubuntu.com/ubuntu xenial/universe all Packages
Ign:26 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en_US
Ign:27 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en
Ign:28 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:29 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:30 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
Ign:31 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
Ign:32 http://archive.ubuntu.com/ubuntu xenial/multiverse all Packages
Ign:33 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_US
Ign:34 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en
Ign:35 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:36 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons
Ign:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Ign:48 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en
Ign:49 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:50 http://archive.ubuntu.com/ubuntu xenial-updates/restricted DEP-11 64x64 Icons
Ign:51 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Ign:52 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
Ign:53 http://archive.ubuntu.com/ubuntu xenial-updates/universe all Packages
Ign:54 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en_US
Ign:55 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en
Ign:56 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:57 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:58 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
Ign:59 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
Ign:60 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse all Packages
Ign:61 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en_US
Ign:62 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en
Ign:63 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:64 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Ign:76 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en
Ign:77 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:78 http://archive.ubuntu.com/ubuntu xenial-backports/restricted DEP-11 64x64 Icons
Ign:79 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu xenial-backports/universe all Packages
Ign:82 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en_US
Ign:83 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en
Ign:84 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:85 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:86 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages
Ign:87 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages
Ign:88 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse all Packages
Ign:89 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en_US
Ign:90 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en
Ign:91 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:92 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Ign:104 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:105 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted DEP-11 64x64 Icons
Ign:107 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:108 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Ign:109 http://archive.ubuntu.com/ubuntu xenial-security/universe all Packages
Ign:110 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en_US
Ign:111 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en
Ign:112 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:113 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:114 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
Ign:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
Ign:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse all Packages
Ign:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en_US
Ign:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en
Ign:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:120 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Ign:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Ign:20 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en
Ign:21 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:22 http://archive.ubuntu.com/ubuntu xenial/restricted DEP-11 64x64 Icons
Ign:23 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Ign:24 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
Ign:25 http://archive.ubuntu.com/ubuntu xenial/universe all Packages
Ign:26 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en_US
Ign:27 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en
Ign:28 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:29 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:30 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
Ign:31 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
Ign:32 http://archive.ubuntu.com/ubuntu xenial/multiverse all Packages
Ign:33 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_US
Ign:34 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en
Ign:35 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:36 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons
Ign:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Ign:48 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en
Ign:49 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:50 http://archive.ubuntu.com/ubuntu xenial-updates/restricted DEP-11 64x64 Icons
Ign:51 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Ign:52 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
Ign:53 http://archive.ubuntu.com/ubuntu xenial-updates/universe all Packages
Ign:54 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en_US
Ign:55 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en
Ign:56 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:57 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:58 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
Ign:59 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
Ign:60 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse all Packages
Ign:61 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en_US
Ign:62 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en
Ign:63 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:64 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Ign:76 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en
Ign:77 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:78 http://archive.ubuntu.com/ubuntu xenial-backports/restricted DEP-11 64x64 Icons
Ign:79 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu xenial-backports/universe all Packages
Ign:82 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en_US
Ign:83 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en
Ign:84 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:85 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:86 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages
Ign:87 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages
Ign:88 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse all Packages
Ign:89 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en_US
Ign:90 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en
Ign:91 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:92 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Ign:104 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:105 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted DEP-11 64x64 Icons
Ign:107 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:108 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Ign:109 http://archive.ubuntu.com/ubuntu xenial-security/universe all Packages
Ign:110 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en_US
Ign:111 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en
Ign:112 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:113 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:114 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
Ign:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
Ign:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse all Packages
Ign:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en_US
Ign:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en
Ign:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:120 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Ign:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Ign:20 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en
Ign:21 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 DEP-11 Metadata
Ign:22 http://archive.ubuntu.com/ubuntu xenial/restricted DEP-11 64x64 Icons
Ign:23 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
Ign:24 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages
Ign:25 http://archive.ubuntu.com/ubuntu xenial/universe all Packages
Ign:26 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en_US
Ign:27 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en
Ign:28 http://archive.ubuntu.com/ubuntu xenial/universe amd64 DEP-11 Metadata
Ign:29 http://archive.ubuntu.com/ubuntu xenial/universe DEP-11 64x64 Icons
Ign:30 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages
Ign:31 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages
Ign:32 http://archive.ubuntu.com/ubuntu xenial/multiverse all Packages
Ign:33 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en_US
Ign:34 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en
Ign:35 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 DEP-11 Metadata
Ign:36 http://archive.ubuntu.com/ubuntu xenial/multiverse DEP-11 64x64 Icons
Ign:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Ign:48 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en
Ign:49 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 DEP-11 Metadata
Ign:50 http://archive.ubuntu.com/ubuntu xenial-updates/restricted DEP-11 64x64 Icons
Ign:51 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
Ign:52 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
Ign:53 http://archive.ubuntu.com/ubuntu xenial-updates/universe all Packages
Ign:54 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en_US
Ign:55 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en
Ign:56 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata
Ign:57 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons
Ign:58 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages
Ign:59 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages
Ign:60 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse all Packages
Ign:61 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en_US
Ign:62 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en
Ign:63 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata
Ign:64 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse DEP-11 64x64 Icons
Ign:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Ign:76 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en
Ign:77 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 DEP-11 Metadata
Ign:78 http://archive.ubuntu.com/ubuntu xenial-backports/restricted DEP-11 64x64 Icons
Ign:79 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages
Ign:80 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages
Ign:81 http://archive.ubuntu.com/ubuntu xenial-backports/universe all Packages
Ign:82 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en_US
Ign:83 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en
Ign:84 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata
Ign:85 http://archive.ubuntu.com/ubuntu xenial-backports/universe DEP-11 64x64 Icons
Ign:86 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 Packages
Ign:87 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse i386 Packages
Ign:88 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse all Packages
Ign:89 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en_US
Ign:90 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse Translation-en
Ign:91 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata
Ign:92 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse DEP-11 64x64 Icons
Ign:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Ign:104 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en
Ign:105 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 DEP-11 Metadata
Ign:106 http://archive.ubuntu.com/ubuntu xenial-security/restricted DEP-11 64x64 Icons
Ign:107 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
Ign:108 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages
Ign:109 http://archive.ubuntu.com/ubuntu xenial-security/universe all Packages
Ign:110 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en_US
Ign:111 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en
Ign:112 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata
Ign:113 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons
Ign:114 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages
Ign:115 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages
Ign:116 http://archive.ubuntu.com/ubuntu xenial-security/multiverse all Packages
Ign:117 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en_US
Ign:118 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en
Ign:119 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata
Ign:120 http://archive.ubuntu.com/ubuntu xenial-security/multiverse DEP-11 64x64 Icons
Err:9 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Ign:10 http://archive.ubuntu.com/ubuntu xenial/main i386 Packages
Ign:11 http://archive.ubuntu.com/ubuntu xenial/main all Packages
Ign:12 http://archive.ubuntu.com/ubuntu xenial/main Translation-en_US
Ign:13 http://archive.ubuntu.com/ubuntu xenial/main Translation-en
Ign:14 http://archive.ubuntu.com/ubuntu xenial/main amd64 DEP-11 Metadata
Ign:15 http://archive.ubuntu.com/ubuntu xenial/main DEP-11 64x64 Icons
Ign:16 http://archive.ubuntu.com/ubuntu xenial/restricted amd64 Packages
Ign:17 http://archive.ubuntu.com/ubuntu xenial/restricted i386 Packages
Ign:18 http://archive.ubuntu.com/ubuntu xenial/restricted all Packages
Ign:19 http://archive.ubuntu.com/ubuntu xenial/restricted Translation-en_US
Err:37 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Ign:38 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages
Ign:39 http://archive.ubuntu.com/ubuntu xenial-updates/main all Packages
Ign:40 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en_US
Ign:41 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en
Ign:42 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata
Ign:43 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons
Ign:44 http://archive.ubuntu.com/ubuntu xenial-updates/restricted amd64 Packages
Ign:45 http://archive.ubuntu.com/ubuntu xenial-updates/restricted i386 Packages
Ign:46 http://archive.ubuntu.com/ubuntu xenial-updates/restricted all Packages
Ign:47 http://archive.ubuntu.com/ubuntu xenial-updates/restricted Translation-en_US
Err:65 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Ign:66 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages
Ign:67 http://archive.ubuntu.com/ubuntu xenial-backports/main all Packages
Ign:68 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en_US
Ign:69 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en
Ign:70 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata
Ign:71 http://archive.ubuntu.com/ubuntu xenial-backports/main DEP-11 64x64 Icons
Ign:72 http://archive.ubuntu.com/ubuntu xenial-backports/restricted amd64 Packages
Ign:73 http://archive.ubuntu.com/ubuntu xenial-backports/restricted i386 Packages
Ign:74 http://archive.ubuntu.com/ubuntu xenial-backports/restricted all Packages
Ign:75 http://archive.ubuntu.com/ubuntu xenial-backports/restricted Translation-en_US
Err:93 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
  Connection failed [IP: 91.189.88.162 80]
Ign:94 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages
Ign:95 http://archive.ubuntu.com/ubuntu xenial-security/main all Packages
Ign:96 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en_US
Ign:97 http://archive.ubuntu.com/ubuntu xenial-security/main Translation-en
Ign:98 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata
Ign:99 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons
Ign:100 http://archive.ubuntu.com/ubuntu xenial-security/restricted amd64 Packages
Ign:101 http://archive.ubuntu.com/ubuntu xenial-security/restricted i386 Packages
Ign:102 http://archive.ubuntu.com/ubuntu xenial-security/restricted all Packages
Ign:103 http://archive.ubuntu.com/ubuntu xenial-security/restricted Translation-en_US
Reading package lists... Done
W: The repository 'http://archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://archive.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial/main/binary-amd64/Packages  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/binary-amd64/Packages  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-backports/main/binary-amd64/Packages  Connection failed [IP: 91.189.88.162 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/xenial-security/main/binary-amd64/Packages  Connection failed [IP: 91.189.88.162 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.



```

Here is a copy from the sources:
```

cat -n /etc/apt/sources.list
     1  # deb cdrom:[Kubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main multiverse restricted universe
     2
     3  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4  # newer versions of the distribution.
     5  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted
     6  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted
    11  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team, and may not be under a free licence. Please satisfy yourself as to
    15  ## your rights to use the software. Also, please note that software in
    16  ## universe WILL NOT receive any review or updates from the Ubuntu security
    17  ## team.
    18  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial universe
    19  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial universe
    20  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates universe
    21  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates universe
    22
    23  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24  ## team, and may not be under a free licence. Please satisfy yourself as to 
    25  ## your rights to use the software. Also, please note that software in 
    26  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27  ## security team.
    28  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial multiverse
    29  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial multiverse
    30  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates multiverse
    31  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    32
    33  ## N.B. software from this repository may not have been tested as
    34  ## extensively as that contained in the main release, although it includes
    35  ## newer versions of some applications which may provide useful features.
    36  ## Also, please note that software in backports WILL NOT receive any review
    37  ## or updates from the Ubuntu security team.
    38  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse
    39  # deb-src [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    40
    41  ## Uncomment the following two lines to add software from Canonical's
    42  ## 'partner' repository.
    43  ## This software is not part of Ubuntu, but is offered by Canonical and the
    44  ## respective vendors as a service to Ubuntu users.
    45  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    46  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    47
    48  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted
    49  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    50  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security universe
    51  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    52  deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security multiverse
    53  # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse

```

I don't know much about Linux (and operating systems in general) but as  additional information I can add that I was living in Mexico, I moved  abroad and my I had problems connecting to Mexico's server, so I tried  to change sources. Everthing worked fine until today, I tried to update  and the terminal started to download this unusual quantity of repo  content.

---

### Post by QIII on 2016-09-21
Hello!

Whatever you meant to give us in your forst example was not saved.  I have given you code tags between which to place the output.

Cheers!

---

### Post by dafhorz on 2016-09-21
For some reason  I can't write in it. When I paste my code it says that "The message you have entered is too short. Please lengthen your message to at least 1 characters."

Edit: Done!

---

### Post by dafhorz on 2016-09-26
Help? Anybody?

---

### Post by ian-weisser on 2016-09-26
Did the problem only occur once, or does it happen every time?

---

### Post by dafhorz on 2016-09-27
This happens everytime that I try to update. In fact, the terminal says it's only a 3% of all the content when the problem occurs and then stops.

---

### Post by ian-weisser on 2016-09-27
That's a lot of 'Ingores' and IP errors during the apt update.
Is your internet connection through some kind of proxy?
Is your internet connection otherwise working properly?

If you internet connection is working properly, and you are not operating through a proxy, try changing mirrors in System Settings --> Software and Updates

---

### Post by dafhorz on 2016-09-29
Yes, you were right, The university where I study makes us connect through a proxy. I tried updating out of the networks I usually use and it worked. 
Thank you very much!

---

### Post by ian-weisser on 2016-09-29
See [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)
for help setting up apt to work through your University proxy.

---

