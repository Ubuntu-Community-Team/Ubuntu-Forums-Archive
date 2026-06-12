---
title: "UIbuntu 14.04 unable to use update or software centre"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by davegeecar on 2014-08-20
I am a new Ubuntu user and until now very happy. Unfortunately I heeded the prompts I was receiving and eventually downloaded 14.04 and installed it. I now have a desktop with a"No Entry" sign at the top and cannot access Updates or the Ubuntu Software Centre. I'm thinking of re-installing 14.04 but I always have problems installing on Linux, I do have a Mint 16 disk here and wonder if I could use that to instal Mint 16 instead of Linux? Help please.

---

### Post by ibjsb4 on 2014-08-20
Please post the output of:
```
sudo apt-get update
```
And what are your computer specs?

---

### Post by davegeecar on 2014-08-20
```
david@david-Dell-DC051:~$ sudo apt-get update
[sudo] password for david: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security InRelease
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty Release.gpg
Get:1 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates Release.gpg [933 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources     
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages
Get:2 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security Release.gpg [933 B]
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty Release   
Get:3 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates Release [59.7 kB]
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports Release
Get:4 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security Release [59.7 kB]
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Sources                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Sources
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Translation-en_GB
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Translation-en_GB
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Translation-en_GB
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Translation-en_GB
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Translation-en
Get:5 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main Sources [108 kB]
Get:6 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted Sources [1,408 B]
Get:7 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe Sources [74.9 kB]
Get:8 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse Sources [3,230 B]
Get:9 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main i386 Packages [289 kB]
Get:10 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted i386 Packages [5,820 B]
Get:11 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe i386 Packages [182 kB]
Get:12 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse i386 Packages [8,437 B]
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse Sources
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse i386 Packages
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe Translation-en
Get:13 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main Sources [39.6 kB]
Get:14 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted Sources [14 B]
Get:15 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe Sources [11.3 kB]
Get:16 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse Sources [699 B]
Get:17 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main i386 Packages [125 kB]
Get:18 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted i386 Packages [14 B]
Get:19 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe i386 Packages [46.1 kB]
Get:20 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse i386 Packages [1,398 B]
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted Translation-en
Hit [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe Translation-en
Fetched 1,018 kB in 4s (232 kB/s)
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
david@david-Dell-DC051:~$ 
```

Memory 2.9 gig
Processor  Intel® Pentium(R) 4 CPU 3.00GHz × 2 
Graphics  Intel® 915G x86/MMX/SSE2
OS Type 32-bit
Disk  286.62 GB

Thanks for replying,  Dave.

---

### Post by ibjsb4 on 2014-08-20
Try this and see what happens next

```
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by ibjsb4 on 2014-08-20
code tags

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by davegeecar on 2014-08-20
david@david-Dell-DC051:~$ sudo rm -r /var/lib/apt/lists
[sudo] password for david: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
rm: cannot remove &#8216;/var/lib/apt/lists&#8217;: No such file or directory
david@david-Dell-DC051:~$ 

david@david-Dell-DC051:~$ sudo mkdir -p /var/lib/apt/lists/partial
[sudo] password for david: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
david@david-Dell-DC051:~$ 

david@david-Dell-DC051:~$ sudo apt-get update
[sudo] password for david: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty InRelease
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates InRelease
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports InRelease
Ign [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease        
Get:1 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty Release.gpg [933 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]
Get:3 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates Release.gpg [933 B]
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release [11.9 kB]
Get:5 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports Release.gpg [933 B]
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources [14 B]
Get:7 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security Release.gpg [933 B]
Get:8 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages [14 B]
Get:9 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty Release [58.5 kB]
Get:10 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates Release [59.7 kB]   
Get:11 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports Release [59.7 kB]
Get:12 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security Release [59.7 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_GB                
Get:13 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Sources [1,064 kB]    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Get:14 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Sources [5,433 B]
Get:15 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Sources [6,399 kB]
Get:16 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Sources [174 kB]     
Get:17 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main i386 Packages [1,348 kB]   
Get:18 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted i386 Packages [13.4 kB]
Get:19 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe i386 Packages [5,866 kB]
Get:20 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse i386 Packages [134 kB]
Get:21 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Translation-en_GB [96.8 kB]
Get:22 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/main Translation-en [762 kB]    
Get:23 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Translation-en_GB [98.3 kB]
Get:24 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/multiverse Translation-en [102 kB]
Get:25 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Translation-en_GB [3,483 B]
Get:26 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/restricted Translation-en [3,457 B]
Get:27 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Translation-en_GB [7,557 B]
Get:28 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty/universe Translation-en [4,089 kB]
Get:29 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main Sources [108 kB]   
Get:30 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted Sources [1,408 B]
Get:31 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe Sources [74.9 kB]
Get:32 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse Sources [3,230 B]
Get:33 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main i386 Packages [289 kB]
Get:34 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted i386 Packages [5,820 B]
Get:35 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe i386 Packages [182 kB]
Get:36 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse i386 Packages [8,437 B]
Get:37 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/main Translation-en [129 kB]
Get:38 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/multiverse Translation-en [4,599 B]
Get:39 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/restricted Translation-en [1,736 B]
Get:40 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-updates/universe Translation-en [89.0 kB]
Get:41 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main Sources [3,524 B]
Get:42 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted Sources [14 B]
Get:43 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe Sources [11.0 kB]
Get:44 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse Sources [768 B]
Get:45 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main i386 Packages [5,198 B]
Get:46 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted i386 Packages [14 B]
Get:47 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe i386 Packages [14.5 kB]
Get:48 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse i386 Packages [619 B]
Get:49 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/main Translation-en [3,409 B]
Get:50 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/multiverse Translation-en [307 B]
Get:51 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/restricted Translation-en [14 B]
Get:52 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-backports/universe Translation-en [9,469 B]
Get:53 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main Sources [39.6 kB] 
Get:54 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted Sources [14 B]
Get:55 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe Sources [11.3 kB]
Get:56 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse Sources [699 B]
Get:57 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main i386 Packages [125 kB]
Get:58 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted i386 Packages [14 B]
Get:59 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe i386 Packages [46.1 kB]
Get:60 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse i386 Packages [1,398 B]
Get:61 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/main Translation-en [62.6 kB]
Get:62 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/multiverse Translation-en [587 B]
Get:63 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/restricted Translation-en [14 B]
Get:64 [http://mirror.sov.uk.goscomb.net](http://mirror.sov.uk.goscomb.net) trusty-security/universe Translation-en [26.4 kB]
Fetched 21.7 MB in 40s (531 kB/s)                                              
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
david@david-Dell-DC051:~$ 

Here is the output from each of those commands.
Dave Williams

---

### Post by ibjsb4 on 2014-08-20
Check this out

[http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)

Found that here

[https://www.google.com/search?client=ubuntu&channel=fs&q=no+talloc+stackframe+at+..%2Fsource3%2Fparam%2Floadparm.c%3A4864%2C+leaking+memory&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=no+talloc+stackframe+at+..%2Fsource3%2Fparam%2Floadparm.c%3A4864%2C+leaking+memory&ie=utf-8&oe=utf-8)

---

### Post by davegeecar on 2014-08-21
Hi Bud, first I would like to thank you very much for your help, it is really appreciated by me as I am following up all the leads you have provided. I have been very busy today and unable to continue with the quest, but I will be back at it tomorrow.
Big Dave.

---

### Post by davegeecar on 2014-08-24
This got rid of my &#8220;No Entry&#8221; sign and got Update Manager and Software Centre working at last, thank you Mark Rijckenberg (markrijckenberg)
 

 Do this first:
 

 First make sure that update-manager, synaptic, etc... are all closed and not running somewhere.
 

 Then open a Terminal and enter the following commands:
 

 sudo rm /var/lib/dpkg/status
 sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
 sudo rm -rf /var/lib/apt/lists/*
 sudo dpkg --configure -a
 sudo aptitude update
 sudo aptitude upgrade
 sudo aptitude install -f
 

 After that, retry opening update-manager.
 

 Regards,
 

 Mark
 

 Any remaining problems do this next:
 

 Hi,
 

 First make sure that update-manager, synaptic, etc... are all closed and not running somewhere.
 

 Then open a Terminal and enter the following commands:
 

 sudo mkdir /var/lib/apt/lists/partial
 sudo dpkg --configure -a
 sudo apt update
 sudo apt upgrade
 sudo apt install -f
 

 After that, retry opening update-manager.
 

 Regards,
 

 Mark
 

 Mark Rijckenberg (markrijckenberg) said on 2009-04-06:


Thank you Ibjsb4 for your help which got me started on this quest.

---

### Post by ibjsb4 on 2014-08-24
Good show :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by davegeecar on 2014-08-24
If anybody is thinking of upgrading to 14.04 I advise against. I have had a week of total aggravation and now have a PC that takes exactly 3 minutes to boot whereas on 12.04 it took about 20 seconds.

---

