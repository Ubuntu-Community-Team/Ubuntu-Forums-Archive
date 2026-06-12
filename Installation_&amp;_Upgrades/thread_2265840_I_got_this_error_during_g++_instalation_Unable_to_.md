---
title: "I got this error during g++ instalation Unable to lock the administration directory ("
date: 2015-02-18
forum: Installation &amp; Upgrades
---

### Post by dzeq on 2015-02-18
Hi,
I can't install g++ properly.

Full log is here

```


dzeq@ing85:~$ g++
The program 'g++' is currently not installed. You can install it by typing:
sudo apt-get install g++
dzeq@ing85:~$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  g++-4.8 libstdc++-4.8-dev
Suggested packages:
  g++-multilib g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg
  libstdc++-4.8-doc
The following NEW packages will be installed:
  g++ g++-4.8 libstdc++-4.8-dev
0 upgraded, 3 newly installed, 0 to remove and 314 not upgraded.
1 not fully installed or removed.
Need to get 0 B/8082 kB of archives.
After this operation, 28,3 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up install-info (5.2.0.dfsg.1-2) ...
Ign http://pl.archive.ubuntu.com trusty InRelease
Ign http://pl.archive.ubuntu.com trusty-updates InRelease
Ign http://extras.ubuntu.com trusty InRelease  
Ign http://pl.archive.ubuntu.com trusty-backports InRelease
Hit http://pl.archive.ubuntu.com trusty Release.gpg
Hit http://pl.archive.ubuntu.com trusty-updates Release.gpg
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://pl.archive.ubuntu.com trusty-backports Release.gpg
Hit http://pl.archive.ubuntu.com trusty Release
Hit http://pl.archive.ubuntu.com trusty-updates Release                        
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://pl.archive.ubuntu.com trusty-backports Release                      
Hit http://pl.archive.ubuntu.com trusty/main Sources                  
Hit http://pl.archive.ubuntu.com trusty/restricted Sources                     
Hit http://pl.archive.ubuntu.com trusty/universe Sources                       
Hit http://pl.archive.ubuntu.com trusty/multiverse Sources           
Hit http://extras.ubuntu.com trusty/main Sources
Hit http://pl.archive.ubuntu.com trusty/main i386 Packages
Hit http://pl.archive.ubuntu.com trusty/restricted i386 Packages     
Hit http://pl.archive.ubuntu.com trusty/universe i386 Packages       
Hit http://extras.ubuntu.com trusty/main i386 Packages               
Hit http://pl.archive.ubuntu.com trusty/multiverse i386 Packages     
Hit http://pl.archive.ubuntu.com trusty/main Translation-en          
Hit http://pl.archive.ubuntu.com trusty/multiverse Translation-en    
Ign http://security.ubuntu.com trusty-security InRelease             
Hit http://pl.archive.ubuntu.com trusty/restricted Translation-en    
Hit http://pl.archive.ubuntu.com trusty/universe Translation-en
Hit http://pl.archive.ubuntu.com trusty-updates/main Sources         
Hit http://pl.archive.ubuntu.com trusty-updates/restricted Sources   
Hit http://pl.archive.ubuntu.com trusty-updates/universe Sources     
Hit http://pl.archive.ubuntu.com trusty-updates/multiverse Sources   
Hit http://pl.archive.ubuntu.com trusty-updates/main i386 Packages   
Hit http://pl.archive.ubuntu.com trusty-updates/restricted i386 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en              
Hit http://pl.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://pl.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://pl.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://pl.archive.ubuntu.com trusty-updates/multiverse Translation-en
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://pl.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://pl.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/main Sources
Hit http://pl.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://pl.archive.ubuntu.com trusty-backports/universe Sources
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://pl.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/restricted i386 Packages
Get:2 http://security.ubuntu.com trusty-security Release [62,0 kB]
Hit http://pl.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://pl.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://pl.archive.ubuntu.com trusty-backports/universe Translation-en
Get:3 http://security.ubuntu.com trusty-security/main Sources [70,4 kB]
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [2061 B]
Get:5 http://security.ubuntu.com trusty-security/universe Sources [17,9 kB]
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [1896 B]
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [205 kB]
Get:8 http://security.ubuntu.com trusty-security/restricted i386 Packages [8846 B]
Get:9 http://security.ubuntu.com trusty-security/universe i386 Packages [87,3 kB]
Get:10 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3624 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Fetched 460 kB in 6s (72,7 kB/s)                                               
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dpkg: error processing package install-info (--configure):
 subprocess installed post-installation script returned error exit status 100
E: Sub-process /usr/bin/dpkg returned an error code (1)
dzeq@ing85:~$ 


```
Any suggestions what can I do ?

---

### Post by kc1di on 2015-02-18
A couple things did you have another package manager open?  if so you need to close that first. 
Second Try running this is a terminal```
sudo dpkg --configure -a
```

If that does not work try this and try the install again:
```
sudo apt-get autoclean
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
```

Then

```
sudo apt-get update
```
Then try install again. 
good luck :)

---

### Post by dzeq on 2015-02-19
:) Thank you for your help. I  made : 

```
sudo apt-get autoclean
sudo apt-get clean
 sudo rm /var/lib/apt/lists/* -vf

```

and it works now.

---

