---
title: "update problem"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by amazoohwawa on 2010-01-08
everytime i try to update i get the following:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

and therefore i am unable to perform many tasks.

this is a clean install of 9.10 on a brand new laptop

---

### Post by Soul-Sing on 2010-01-08
And if you change via software sources: settings: change the server to main server in ubuntu software tab?
If this doesn't help, post the results of ```
sudo apt-get update
```, ```
sudo apt-get upgrade
```

---

### Post by amazoohwawa on 2010-01-08
jim@acer-linux:~$ sudo apt-get update
[sudo] password for jim: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                     
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [914B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release [44.1kB]           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release 
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security/multiverse Sources               
Fetched 4,023B in 6s (614B/s)                                                  
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
jim@acer-linux:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jim@acer-linux:~$

---

### Post by Soul-Sing on 2010-01-08
maybe this thread would be helpful: [http://ubuntuforums.org/showthread.php?t=1152619](http://ubuntuforums.org/showthread.php?t=1152619)
(it is a copy of your problem.)

---

### Post by amazoohwawa on 2010-01-08
this is what i get now:

E: Could not open lock file /var/lib/apt/lists/lock - open (2: No such file or directory)
E: Unable to lock the list directory

---

### Post by Soul-Sing on 2010-01-08
do you have any other packagemanagers open? please them and try again via sudo apt-get etc
if not: ```
sudo rm -rf /var/lib/apt/lists/lock
```
```
sudo apt-get update
```

---

