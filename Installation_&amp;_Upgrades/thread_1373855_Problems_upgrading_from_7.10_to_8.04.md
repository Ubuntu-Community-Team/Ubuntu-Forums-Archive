---
title: "Problems upgrading from 7.10 to 8.04"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by gisrob on 2010-01-06
Hi

I've got a Viglen L-MPC low power PC that I have recently upgraded from Feisty to Gutsy using the instructions at

[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)

I'm now trying to follow the instructions to upgrade to Hardy.

[https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

but am hitting a problem that I can't see anywhere else.  I know I am some years behind the curve here, so I think that my problems are due to the repositories, but would appreciate any guidance or advice you can offer.

As per the instructions, I checked my linux version[INDENT]$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
[/INDENT]and modified my sources.list file 
[INDENT]$ cat /etc/apt/sources.list
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
[/INDENT]I then started the upgrade.
[INDENT]$ sudo aptitude update && sudo aptitude safe-upgrade
Get:1 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release.gpg [191B]
Get:2 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/main Translation-en_GB [21.3kB]
Get:3 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/restricted Translation-en_GB [2395B]
Get:4 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/universe Translation-en_GB [4405B]
Get:5 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/multiverse Translation-en_GB [8133B]
Get:6 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release.gpg [189B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/main Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/restricted Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/universe Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/multiverse Translation-en_GB
Get:7 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security Release.gpg [189B]
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/main Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/restricted Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/universe Translation-en_GB
Ign [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/multiverse Translation-en_GB
Get:8 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy Release [65.9kB]
Get:9 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates Release [58.5kB]
Get:10 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security Release [58.5kB]
Get:11 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/main Packages [1075kB]            
Get:12 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/restricted Packages [7664B]
Get:13 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/universe Packages [4065kB]
Get:14 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy/multiverse Packages [158kB]                              
Get:15 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/main Packages [309kB]                            
Get:16 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/restricted Packages [6138B]                      
Get:17 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/universe Packages [125kB]                        
Get:18 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-updates/multiverse Packages [13.2kB]                     
Get:19 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/main Packages [152kB]                           
Get:20 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/restricted Packages [5773B]                     
Get:21 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/universe Packages [103kB]                       
Get:22 [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) gutsy-security/multiverse Packages [8316B]                     
Fetched 6247kB in 1m1s (101kB/s)                                                                     
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
[/INDENT]I then changed my sources.list file
[INDENT]$ sudo vi /etc/apt/sources.list

## EOL upgrade sources.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse

# Optional
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

[/INDENT]and started the upgrade
[INDENT]$ sudo do-release-upgrade
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmp8_iDOn/hardy.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 
[/INDENT]but with no success.

Any clues as to what this might be, or how I can upgrade my linux to a suitably supported version?  The Viglen box does have USB drives, but I have had similar success (i.e., none) in installing clean from a Jaunty USB image.

I have no data that needs to be saved on this box, so am happy to do a clean install if there is an easy way of doing it!

Many thanks in advance

Rob

---

### Post by slakkie on 2010-01-06
I think you hit the bull's eye:

> 
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Mac users may have some difficulty upgrading to the most current release around versions 7.04/7.10. 

You are using PPC or Intel based Macs? AFAIK Ubuntu stopped with PPC binaries a while ago. Those binary packages where found on ports.ubuntu.com.

If you are running Intel Mac you should be able to use the normal repositories at archive.ubuntu.com (for supported versions off course).

I don't have enough knowledge about Mac and Ubuntu (my girlfriend won't let me install Ubuntu on her Macbook..).

You could have a look here: [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads) 

Please tell me if you find a good upgrade solution, so I can add it to the EOLupgrade page. Many thanks!

---

### Post by gisrob on 2010-01-06
I'm not using PPC or a Mac.  Its a Viglen MPC-L (typo in OP) which uses an AMD Geode processor.

---

### Post by slakkie on 2010-01-06
Ahh, did you run sudo aptitude update after you updated your sources.list?

I see that step was missing in the tutorial, updated it.

---

### Post by gisrob on 2010-01-06
I hadn't run sudo aptitude update, but I have done now, and I'm still getting the same error message downloading the tar file.

---

### Post by slakkie on 2010-01-06
> **gisrob said:**
> I hadn't run sudo aptitude update, but I have done now, and I'm still getting the same error message downloading the tar file.

Mmmm, not good. What you could do is download the alternate CD and upgrade your PC via that. See also [https://help.ubuntu.com/community/Upgrades#Upgrades%20via%20alternate%20CD](https://help.ubuntu.com/community/Upgrades#Upgrades%20via%20alternate%20CD)

---

