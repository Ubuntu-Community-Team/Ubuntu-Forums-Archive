---
title: "libc6 exit status 135?"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by reidsimmons on 2007-11-30
So it all started when I tried to automatically get updates, a popup met me with the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


So I did as it said:

root@ORION:/home/reid# dpkg --configure -a
root@ORION:/home/reid# 

All looks good, no?  So I go back to get my updates, and it seems to go well, until I get to libc6, where I get the following:

Setting up libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:

...and that was it.

How can I make libc6 install properly?  Everything was working just fine before now...

---

### Post by Pumalite on 2007-11-30
sudo dpkg -configure -a

---

### Post by reidsimmons on 2007-11-30
was running the terminal as root already, but tried sudo, with the same results.

---

### Post by Pumalite on 2007-11-30
Post the output of:
sudo dpkg --configure -a

---

### Post by reidsimmons on 2007-12-01
reid@ORION:~$ sudo dpkg --configure -a
[sudo] password for reid:
reid@ORION:~$ 

it gives no output, simply returns me to the command prompt.

---

### Post by Pumalite on 2007-12-01
Run:
sudo apt-get update
sudo apt-get upgrade

---

### Post by reidsimmons on 2007-12-02
reid@ORION:~$ sudo apt-get update
[sudo] password for reid:
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release.gpg                                
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release [6998B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release.gpg [191B]          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports Release [44.0kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                     
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages           
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                      
Get:9 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages [2359B]     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Get:10 [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources [1291B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Packages [13.3kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Packages [14B]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Packages [48.3kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Packages [2599B]
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Translation-en_US                 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/main Sources [4929B]   
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/restricted Sources [14B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/universe Sources [9480B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-backports/multiverse Sources [832B]
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable Release        
Ign [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages
Hit [http://blognux.free.fr](http://blognux.free.fr) unstable/main Packages
Fetched 134kB in 4s (29.7kB/s)
Reading package lists... Done
reid@ORION:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  firefox firefox-gnome-support k3b libk3b2 libpcre3 libpcrecpp0
  libpoppler-glib2 libpoppler2 libpurple0 pidgin pidgin-data poppler-utils
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
reid@ORION:~$

---

### Post by Pumalite on 2007-12-02
Is Synaptic closed while you do this?

---

### Post by reidsimmons on 2007-12-02
yes, it is closed, aling with update notifier and anything else update/install-related.

---

### Post by mgor on 2007-12-30
I had the same problem after trying to remove gnokii.

I solved it by reinstalling the package containing the library that ldconfig gets the "bus error" on.

If you run
```
strace ldconfig
```

You will see a system call to open with a path to a library, check the last call to open before the bus error. In my case it was libfuse2 that was the problem. It would look something like the example below.
```
open("/lib/libfuse2.so.2.7.0", O_RDONLY) = 4
```

Check which package that owns that file
```
dpkg -S /lib/libfuse2.so.2.7.0
```

Then just reinstall that package and make sure it works by running "ldconfig". If you did not get any error messages, go ahead and run "dpkg --configure -a", and you're all set!

---

