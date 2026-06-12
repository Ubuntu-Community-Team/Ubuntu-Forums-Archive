---
title: "/var/lib/dkpg/status is messed up."
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by Haydn King on 2008-05-26
Hi,
I installed Hardy Heron the other day (having been using Fedora 7/8/9), and was very impressed - Ubuntu does seem to 'just work'!

That was until i started getting errors when I started synaptic -
```
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

or apt-get
```
hjk@HJK-Ubuntu:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB                  
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB            
Hit http://archive.ubuntu.com hardy Release.gpg                                
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB              
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB          
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB    
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB      
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy Release                                    
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_GB     
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB     
Hit http://gb.archive.ubuntu.com hardy Release                                 
Hit http://archive.canonical.com hardy Release                                 
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://gb.archive.ubuntu.com hardy-updates Release                         
Hit http://archive.ubuntu.com hardy/main Sources                               
Hit http://gb.archive.ubuntu.com hardy/main Packages                           
Hit http://gb.archive.ubuntu.com hardy/restricted Packages                     
Hit http://gb.archive.ubuntu.com hardy/restricted Sources                      
Hit http://archive.ubuntu.com hardy/restricted Sources                         
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://gb.archive.ubuntu.com hardy/main Sources                  
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages           
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages         
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages   
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/multiverse Sources     
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources    
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources          
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources    
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources      
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages     
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages   
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://archive.canonical.com hardy/partner Sources
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
```

I've done a lot of googleing, copied /var/lib/dkpg/status-old to status, run a few commands, eg

```
hjk@HJK-Ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 2:
 MSDOS EOF (^Z) in field name `
```

Then i tried to look at /var/lib/dpkg/status, but gedit just griped "gedit has not been able to detect the character coding...". I built emacs from source (not having a package manager atm), and the file appears garbled - as is status-old.

The only ways out I can think of are
a) generating a new status file somehow, or
b) reinstalling apt-get somehow
c) reinstalling the entire OS

I really don't want to have to do c - what do i do next time it happens?

This seems to be a fairly common problem, so maybe someone has another way of solving it...

Thanks in advance,
Haydn King

---

### Post by sisco311 on 2008-05-26
from the terminal:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```

d) replace the corrupted file with a backup :)

---

### Post by Haydn King on 2008-05-26
> **sisco311 said:**
> from the terminal:
```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo aptitude update
```

d) replace the corrupted file with a backup :)
I tried it and got
```
hjk@HJK-Ubuntu:/media/Disk/00LINUX/HJK/Videos$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
[sudo] password for hjk: 
hjk@HJK-Ubuntu:/media/Disk/00LINUX/HJK/Videos$ sudo aptitude update
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://gb.archive.ubuntu.com hardy Release.gpg                  
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB                   
Hit http://archive.canonical.com hardy Release.gpg                              
Ign http://archive.canonical.com hardy/partner Translation-en_GB                
Hit http://security.ubuntu.com hardy-security Release.gpg                       
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB            
Hit http://archive.ubuntu.com hardy Release                                     
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB             
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB    
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB  
Hit http://gb.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://gb.archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Hit http://archive.canonical.com hardy Release                       
Hit http://gb.archive.ubuntu.com hardy Release                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release
Hit http://gb.archive.ubuntu.com hardy-updates Release             
Hit http://archive.ubuntu.com hardy/main Sources                    
Hit http://archive.canonical.com hardy/partner Packages             
Hit http://archive.ubuntu.com hardy/restricted Sources                          
Hit http://archive.canonical.com hardy/partner Sources                          
Hit http://gb.archive.ubuntu.com hardy/main Packages                            
Hit http://security.ubuntu.com hardy-security/main Packages         
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy-updates/main Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://gb.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://gb.archive.ubuntu.com hardy-updates/main Sources
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Sources
Hit http://gb.archive.ubuntu.com hardy-updates/universe Packages
Hit http://gb.archive.ubuntu.com hardy-updates/multiverse Packages
Reading package lists... Error!
E: Unable to parse package file /var/lib/dpkg/status (1)
E: The package lists or status file could not be parsed or opened.
E: Couldn't rebuild package cache

```

(87178291199 is prime!)

---

### Post by sisco311 on 2008-05-26
I have found more backups in the /var/backups directory. First you need to extract the files:
```
sudo gunzip /var/backups/dpkg.status.*.gz
``````
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo aptitude update
```If doesn't work try the next backup:

```
sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status
sudo aptitude update
```
and so on...

I hope one will work.

---

### Post by Haydn King on 2008-05-26
Bingo! That worked! - everything seems fine now!

/var/backups/dpkg/status is now a plain text file again!

Thanks a lot for your help!

---

