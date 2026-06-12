---
title: "Issue installing Ubuntu 7.04: The update program freezes with the following error:"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by acobon on 2007-04-28
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz) Sub-process gzip returned an error code (1)

Odd. Any ideas on how to fix it?

I have a dial-up connection. So I restarted that. Then I tried rebooting my computer. No luck.
After that I went into Synaptic and in the preferences window I had the program delete the cached files (Hoping to force the update agent to give the files another chance to download.) No luck. :confused:

---

### Post by acobon on 2007-04-28
Sorry, I looked farther into the forum and found another way to install it. I still got the same error but I was able to get more information.

from aptitude running the update command

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [3559kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources [365kB]
99% [5 Sources gzip 0] [4 Packages bzip2 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources
  Sub-process gzip returned an error code (1)
99% [4 Packages bzip2 0]                   
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process bzip2 returned an error code (2)
Fetched 5B in 5s (1B/s) 
Reading package lists... Done

---

