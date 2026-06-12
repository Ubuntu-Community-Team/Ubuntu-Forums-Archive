---
title: "nvidia-glx installation error"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by turtlepaul on 2008-04-06
I've been having problems with my video card. I haven't been able to play certain games. I tried to install nvidia-glx but it gave me an error. Synaptic said this:

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb: subprocess pre-installation script returned error exit status 2

I looked around for something to do. I ran:

```
paul@paul-desktop:~$ sudo apt-get install linux-restricted-modules-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-2.6.22-14-generic is already the newest version.
linux-restricted-modules-2.6.22-14-generic set to manual installed.
The following packages were automatically installed and are no longer required:
  alien-arena-data tremulous-data libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

and then 

```
paul@paul-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  alien-arena-data tremulous-data libsdl-ttf2.0-0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4493kB of archives.
After unpacking 13.7MB of additional disk space will be used.
(Reading database ... 190463 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: error processing /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone help me?

---

### Post by Rocket2DMn on 2008-04-06
Try
```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```
Then try using the restricted drivers from System->Administration->Restricted Drivers Manager
Post back any errors you get, if any.

---

### Post by turtlepaul on 2008-04-08
I got an error at the third line:

```
paul@paul-desktop:~$ sudo apt-get update
Get:1 http://archive.canonical.com gutsy Release.gpg [191B]
Ign http://archive.canonical.com gutsy/partner Translation-en_US
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Hit http://archive.canonical.com gutsy Release                       
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US  
Hit http://security.ubuntu.com gutsy-security Release                          
Get:4 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US
Get:5 http://wine.budgetdedicated.com gutsy Release.gpg [191B]     
Ign http://wine.budgetdedicated.com gutsy/main Translation-en_US   
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://wine.budgetdedicated.com gutsy Release                              
Hit http://archive.canonical.com gutsy/partner Packages                        
Hit http://security.ubuntu.com gutsy-security/main Packages
Hit http://security.ubuntu.com gutsy-security/restricted Packages   
Hit http://security.ubuntu.com gutsy-security/universe Packages     
Hit http://security.ubuntu.com gutsy-security/multiverse Packages   
Err http://wine.budgetdedicated.com gutsy Release                   
  
Hit http://us.archive.ubuntu.com gutsy/main Packages               
Hit http://security.ubuntu.com gutsy-security/main Sources
Hit http://security.ubuntu.com gutsy-security/restricted Sources
Hit http://security.ubuntu.com gutsy-security/universe Sources
Hit http://security.ubuntu.com gutsy-security/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Get:6 http://wine.budgetdedicated.com gutsy Release [1005B]
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Ign http://wine.budgetdedicated.com gutsy Release
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Ign http://wine.budgetdedicated.com gutsy/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://wine.budgetdedicated.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://wine.budgetdedicated.com gutsy/main Packages
Fetched 1200B in 1s (943B/s)
Reading package lists... Done
W: GPG error: http://wine.budgetdedicated.com gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

```

---

### Post by Rocket2DMn on 2008-04-08
Try going to System->Administration->Software Sources, hitting the Third-Party Software tab and disabling your winehq stuff, then try again.  Afterwards you can add the winehq stuff back by following the directions here: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

You should be able to proceed with wine warning anyway, it just won't check there for updates.

---

