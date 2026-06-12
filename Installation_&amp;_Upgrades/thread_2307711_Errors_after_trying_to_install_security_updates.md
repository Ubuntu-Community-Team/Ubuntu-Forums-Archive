---
title: "Errors after trying to install security updates"
date: 2015-12-27
forum: Installation &amp; Upgrades
---

### Post by jon-williams1970 on 2015-12-27
Hi All

Would be grateful for any help - I have had various Ubuntu releases for several years and have usually been able to fix any problems after a little research, but this problem has me stuck..!

I'm running Ubuntu 12.04 LTS 64-bit

I attempted the Important Security Updates a few weeks ago, and received this error message:

> The following packages have unmet dependencies:

libk5crypto3: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.12 is installed
libk5crypto3:i386: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.12 is installed

and then on another attempt:

> (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 1508366 files and directories currently installed.) 
Preparing to replace libk5crypto3 1.10+dfsg~beta1-2ubuntu0.6 (using .../libk5crypto3_1.10+dfsg~beta1-2ubuntu0.7_amd64.deb) ... 
De-configuring libk5crypto3:i386 ... 
Unpacking replacement libk5crypto3 ... 
dpkg: unrecoverable fatal error, aborting: 
 fork failed: Cannot allocate memory 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2) 
dpkg: error processing libk5crypto3:i386 (--configure): 
 libk5crypto3:i386 cannot be configured because libk5crypto3:amd64 is not ready for configuration (current status 'half-installed') 
Errors were encountered while processing:

Some things I have attempted to sort out the problem:

 >  sudo apt-get clean
  sudo apt-get autoclean
  sudo apt-get -f install
  sudo dpkg --configure -a
  
  sudo apt-get -u dist-upgrade
  sudo apt-get -o Debug: : pkgProblemResolver=yes dist-upgrade

  sudo aptitude safe-upgrade
  sudo aptitude --safe-resolver


Currently I am unable to use any flash player on webpages, and cannot update anything. I seem to remember at one point an error message said something about 'dpkg' being corrupted, but not sure where to find that message now.

Please help!

Thanks

---

### Post by ian-weisser on 2015-12-28
Please show us the output to:
```
apt-cache policy libk5crypto3
```

---

### Post by jon-williams1970 on 2015-12-28
Hi Ian - thanks for your help

output is:

> libk5crypto3:
  Installed: 1.10+dfsg~beta1-2ubuntu0.7
  Candidate: 1.10+dfsg~beta1-2ubuntu0.7
  Version table:
 *** 1.10+dfsg~beta1-2ubuntu0.7 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.10+dfsg~beta1-2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main amd64 Packages

J

---

### Post by ian-weisser on 2015-12-29
Looks like your original problem has been sorted since you originally noticed it.

> **jon-williams1970 said:**
> The following packages have unmet dependencies:
**libk5crypto3**: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.12 is installed

> **jon-williams1970 said:**
> libk5crypto3:
  **Installed: 1.10+dfsg~beta1-2ubuntu0.7**
  Candidate: 1.10+dfsg~beta1-2ubuntu0.7

libk5crypto3 had a problem, but seems now happily installed.
You said you cannot update...please show us the complete output of:
```
sudo apt update
sudo apt upgrade
```

---

### Post by jon-williams1970 on 2015-12-29
Hi

'sudo apt update'  - gives:

> sudo: apt: command not found

should it be 'apt-get'.....? if i put in 'sudo apt-get update' 

```
jon@jon-desktop:~$ sudo apt-get update
[sudo] password for jon: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                        
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B]      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [196 kB]   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]        
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [54.3 kB]                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [495 kB]
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [8,708 B]     
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [123 kB]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [9,727 B]                 
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main amd64 Packages [967 kB]                 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [138 kB]                        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [4,476 B]                          
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [44.3 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [2,201 B]                            
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [578 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [11.6 kB]                        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [127 kB]                       
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,699 B]                   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [636 kB]                            
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [11.6 kB]                      
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [135 kB]                               
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,875 B]                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex   
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted amd64 Packages [16.2 kB]                 
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe amd64 Packages [270 kB]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en       
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.5 kB]
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [1,026 kB]                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                                 
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [16.1 kB]                 
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [280 kB]
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [16.7 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en
Fetched 5,189 kB in 5s (985 kB/s)                   
Reading package lists... Done

```

....which didn't report any problems - I usually get error messages if I try anything like that!!

I'll just have a look at the Update Manager before I try the upgrade command

---

### Post by jon-williams1970 on 2015-12-29
Hi

Update Manager reports problems still

'sudo apt-get upgrade'  - gives:


> jon@jon-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run &#8216;apt-get -f install&#8217; to correct these.
The following packages have unmet dependencies.
 libk5crypto3 : Breaks: libk5crypto3:i386 (!= 1.10+dfsg~beta1-2ubuntu0.7) but 1.10+dfsg~beta1-2ubuntu0.6 is installed
 libk5crypto3:i386 : Breaks: libk5crypto3 (!= 1.10+dfsg~beta1-2ubuntu0.6) but 1.10+dfsg~beta1-2ubuntu0.7 is installed
E: Unmet dependencies. Try using -f.


J

---

### Post by ian-weisser on 2015-12-29
Try:
```
sudo apt-get clean libk5crypto3                ## Delete the locally caches version, forcing apt to redownload the current version
sudo apt-get install --reinstall libk5crypto3  ## Force apt to upgrade the newest version of the package
```

---

### Post by jon-williams1970 on 2015-12-29
Hi Ian

Here's the result of your suggestion, should I try 'apt-get -f install' again, you think...?

> 
jon@jon-desktop:~$ sudo apt-get clean libk5crypto3
[sudo] password for jon: 
jon@jon-desktop:~$ sudo apt-get install --reinstall libk5crypto3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libk5crypto3 : Breaks: libk5crypto3:i386 (!= 1.10+dfsg~beta1-2ubuntu0.7) but 1.10+dfsg~beta1-2ubuntu0.6 is to be installed
 libk5crypto3:i386 : Breaks: libk5crypto3 (!= 1.10+dfsg~beta1-2ubuntu0.6) but 1.10+dfsg~beta1-2ubuntu0.7 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).




J

---

### Post by oldos2er on 2015-12-29
Thread moved to Installation & Upgrades.

---

### Post by ian-weisser on 2015-12-29
I'm not running 12.04, so things may have changed...but libk5crypto3 and libk5crypto3:i386 conflict in 15.10.
Have you tried removing libk5crypto3:i386?

---

### Post by jon-williams1970 on 2016-01-02
Hi Ian,

Have just removed libk5crypto3:i386 and seems all problems have resolved..!

Thanks very much, this had been an obstacle for weeks! Happy New Year to you!

J

---

