---
title: "Ubuntu software centre broken"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by sbtblab on 2013-01-13
Hi everyone,

This is my first post here, and I'm not entirely sure if this is exactly the right part of the forum to post it, but here goes anyway. As the title suggests I'm having trouble with Ubuntu Software Centre. It seems to have spontaneously started giving me the following problem;

I open USC and get a window which says 
  " Items cannot be installed or repaired until the package catalog is repaired. Do you want to repair it now? Once Update Manger has finished the repairs you can close it and return to the store."

I click on "repair". I authenticate with my password. I am greeted by a window which says
 "Package operation failed. The installation or removal of a software package failed." Fortunately, the window in question also provides the following details

"installArchives() failed: dpkg: dependency problems prevent configuration of evince: 
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.1); however: 
  Version of libevince3-3 on system is 3.4.0-0ubuntu1.4. 
dpkg: error processing evince (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 evince 
Error in function:  
dpkg: dependency problems prevent configuration of evince: 
 evince depends on libevince3-3 (= 3.4.0-0ubuntu1.1); however: 
  Version of libevince3-3 on system is 3.4.0-0ubuntu1.4. 
dpkg: error processing evince (--configure): 
 dependency problems - leaving unconfigured"

And I'm stuck. :-k

And just to make things even more amusing, when I click on "okay", the whole process repeats itself. Same windows come up, same error message, ad infinitum.

Help! Please? Hopefully with idiot-proof step-by-step instructions.

Oh yeah, this is Ubuntu 12.04 LTS

Thanks in advance!

---

### Post by JRV on 2013-01-13
Welcome aboard!

Please post a copy of your /etc/apt/sources.list file.

Run the command:
```

sudo apt-get update

```
and post the error messages.

---

### Post by sbtblab on 2013-01-14
Hi, and thanks for your help!

I ran 
  sudo apt-get update
and surprisingly got no (obvious) error messages. What I did get was this;

Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg         
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release [49.6 kB]              
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [214 kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages [449 kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [60.5 kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages [8,366 B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages [166 kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,654 B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages [457 kB]   
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages [8,374 B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages [168 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,184 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [221 kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages [9,678 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en        
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en [99.2 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [61.5 kB]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,366 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [37.3 kB]
Fetched 2,092 kB in 12s (167 kB/s)                                             
Reading package lists... Done

Which looked like no problem to me. The contents of /etc/apt/sources.list read as follows;

# /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse

And yet the problem with Software Centre persists. 

Cheers!

---

### Post by JRV on 2013-01-14
You have an incomplete /etc/apt/sources.list file.

Mine loooks like this:
```

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

```

Make a backup of your file and replace it with this.

---

### Post by sbtblab on 2013-01-14
Thanks JRV, replacing the sources.list seems to have done the trick!

Cheers!

---

### Post by JRV on 2013-01-15
Glad I could help.
Please mark your thread as **Solved**.
(Thread tools near the top of the page.)

---

