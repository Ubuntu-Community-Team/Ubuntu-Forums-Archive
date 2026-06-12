---
title: "Sources broken in Mavrick"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by RFXCasey on 2011-04-23
Hi, just installed Ubuntu 10.10 and right off the bat the source.list file seems to be broken. Try to update with 'sudo apt-get update and getting lots of errors.

```
Hit http://us.archive.ubuntu.com maverick Release.gpg
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Get:3 http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Get:4 http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Get:5 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Get:6 http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Get:7 http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Get:8 http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Get:9 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Get:10 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Get:11 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Get:12 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Get:13 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Get:14 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Get:15 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Get:16 http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg
Get:17 http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Get:18 http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Get:19 http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Get:20 http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Get:21 http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Get:22 http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Get:23 http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Get:24 http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-security Release                     
Get:25 http://us.archive.ubuntu.com maverick/main Sources
Err http://us.archive.ubuntu.com maverick/main Sources   
  Undetermined Error
Get:26 http://us.archive.ubuntu.com maverick/restricted Sources
Err http://us.archive.ubuntu.com maverick/restricted Sources
  Undetermined Error
Get:27 http://us.archive.ubuntu.com maverick/universe Sources
Err http://us.archive.ubuntu.com maverick/universe Sources
  Undetermined Error
Get:28 http://us.archive.ubuntu.com maverick/multiverse Sources
Err http://us.archive.ubuntu.com maverick/multiverse Sources
  Undetermined Error
Get:29 http://us.archive.ubuntu.com maverick/main i386 Packages
Err http://us.archive.ubuntu.com maverick/main i386 Packages
  Undetermined Error
Get:30 http://us.archive.ubuntu.com maverick/restricted i386 Packages
Err http://us.archive.ubuntu.com maverick/restricted i386 Packages
  Undetermined Error
Get:31 http://us.archive.ubuntu.com maverick/universe i386 Packages
Err http://us.archive.ubuntu.com maverick/universe i386 Packages
  Undetermined Error
Get:32 http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Err http://us.archive.ubuntu.com maverick/multiverse i386 Packages
  Undetermined Error
Get:33 http://us.archive.ubuntu.com maverick-updates/main Sources
Err http://us.archive.ubuntu.com maverick-updates/main Sources
  Undetermined Error
Get:34 http://us.archive.ubuntu.com maverick-updates/restricted Sources
Err http://us.archive.ubuntu.com maverick-updates/restricted Sources
  Undetermined Error
Get:35 http://us.archive.ubuntu.com maverick-updates/universe Sources
Err http://us.archive.ubuntu.com maverick-updates/universe Sources
  Undetermined Error
Get:36 http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Err http://us.archive.ubuntu.com maverick-updates/multiverse Sources
  Undetermined Error
Get:37 http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Err http://us.archive.ubuntu.com maverick-updates/main i386 Packages
  Undetermined Error
Get:38 http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Err http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
  Undetermined Error
Get:39 http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Err http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
  Undetermined Error
Get:40 http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  Undetermined Error
Get:41 http://us.archive.ubuntu.com maverick-security/main Sources
Err http://us.archive.ubuntu.com maverick-security/main Sources
  Undetermined Error
Get:42 http://us.archive.ubuntu.com maverick-security/restricted Sources
Err http://us.archive.ubuntu.com maverick-security/restricted Sources
  Undetermined Error
Get:43 http://us.archive.ubuntu.com maverick-security/universe Sources
Err http://us.archive.ubuntu.com maverick-security/universe Sources
  Undetermined Error
Get:44 http://us.archive.ubuntu.com maverick-security/multiverse Sources
Err http://us.archive.ubuntu.com maverick-security/multiverse Sources
  Undetermined Error
Get:45 http://us.archive.ubuntu.com maverick-security/main i386 Packages
Err http://us.archive.ubuntu.com maverick-security/main i386 Packages
  Undetermined Error
Get:46 http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
Err http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
  Undetermined Error
Get:47 http://us.archive.ubuntu.com maverick-security/universe i386 Packages
Err http://us.archive.ubuntu.com maverick-security/universe i386 Packages
  Undetermined Error
Get:48 http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
99% [48 Packages bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 2,584B in 7s (359B/s)
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.bz2  Undetermined Error

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

I've tried other sources like main and several others but doesn't seem to make a difference. Why is this broken right out of the box and does anyone know how to fix this. I've installed Linuxs (Debian, Ubuntu, Mint, PClinuxOS) on several other systems so I'm not completely newb. Had sort of the same problem happen once before with Ubuntu but changing sources fixed it. Changing sources isn't working this time.

---

### Post by cantormath on 2011-04-23
It almost looks like you are either not connected to the internet with this machine or the repos are done temporarily.  This is very unusual.  Does the computer update when connected via a ethernet cable? Are you using wireless?

---

### Post by RFXCasey on 2011-04-23
No, this machine is not on a wireless network. Internet access through firefox works fine. I may have neglected to mention the fact that I am running Ubuntu on a virtual machine using VMware player. The problem my not be with Ubuntu then though I have had a similar issue when not running a VM. If you or anyone has experience in this department please share your knowledge.

---

