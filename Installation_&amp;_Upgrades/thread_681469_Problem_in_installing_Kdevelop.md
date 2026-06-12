---
title: "Problem in installing Kdevelop"
date: 2008-01-29
forum: Installation &amp; Upgrades
---

### Post by bargi on 2008-01-29
Hi,

I have a problem in installing Kdevelop....

First I have used Synaptic Package manager to install it but it give error that some packages cannot be fetch .........

So I canceled  it and download kdevelop  3.5  and run ./configure command.....

It give me following error........


checking for kde-config... not found
configure: error: The important program kde-config was not found!
Please check whether you installed KDE correctly.

Can any body help me in installing Kdevelop......

Thanks

---

### Post by forestpixie on 2008-01-29
can you install anything? - open a terminal, paste this in 

cat /etc/apt/sources.list

if the lines are prefixed with #

open software sources and checkall the boxes and uncheck the cdrom

---

### Post by bargi on 2008-01-29
Hi ,

Thanks for reply........

I have apply what u have said but still the same error is there.......

I have tried to install kde-config by using command...

sudo apt-get install kde-config

but it give error :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kde-config

Please let me know where I am wrong........

Thanks'

---

### Post by forestpixie on 2008-01-29
run these and post the output please and can you put them in code tags (# in the post reply)

```
sudo apt-get update
cat /etc/apt/sources.list
```

Edit - I don't actually know if kde-config is a pacakge - I can't find it either, I guess it'spart of kde, though why you can't install it I don't know. I'll have a look into it

Try ```
sudo apt-get install kdevelop
``` again and paste the whole error

---

### Post by bargi on 2008-01-29
Hi ,

The following is the output of command sudo apt-get upgrade:

```

Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]                                                       
Get:2 http://archive.canonical.com gutsy Release.gpg [191B]                                      
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]                                   
Ign http://archive.canonical.com gutsy/partner Translation-en_IN                                     
Ign http://archive.ubuntu.com gutsy/main Translation-en_IN                                        
Hit http://archive.canonical.com gutsy Release                                                   
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN                         
Ign http://archive.ubuntu.com gutsy/universe Translation-en_IN     
Hit http://archive.canonical.com gutsy/partner Packages
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Hit http://archive.canonical.com gutsy/partner Sources
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_IN
Get:4 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN 
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_IN     
Hit http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_IN
Hit http://security.ubuntu.com gutsy-security/universe Packages
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_IN
Hit http://security.ubuntu.com gutsy-security/main Packages
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_IN
Hit http://security.ubuntu.com gutsy-security/multiverse Packages                                                           
Get:5 http://archive.ubuntu.com gutsy-proposed Release.gpg [191B]                                                           
Hit http://security.ubuntu.com gutsy-security/restricted Packages                                                           
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_IN                                                     
Get:6 http://security.ubuntu.com gutsy-security/universe Sources [4750B]                                                    
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_IN                                                         
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_IN                                                   
Get:7 http://security.ubuntu.com gutsy-security/main Sources [11.8kB]                                                       
Ign http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_IN                                                   
Get:8 http://archive.ubuntu.com gutsy-backports Release.gpg [191B]                                                          
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_IN                                                    
Get:9 http://security.ubuntu.com gutsy-security/multiverse Sources [833B]                                                   
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_IN                                                        
Get:10 http://security.ubuntu.com gutsy-security/restricted Sources [14B]                                                   
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_IN                                                  
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_IN                                                  
Hit http://archive.ubuntu.com gutsy Release                                                                                 
Hit http://archive.ubuntu.com gutsy-updates Release                                                                         
Get:11 http://archive.ubuntu.com gutsy-proposed Release [58.5kB]                                                            
Get:12 http://archive.ubuntu.com gutsy-backports Release [44.0kB]                                                           
Hit http://archive.ubuntu.com gutsy/main Packages                                                                           
Hit http://archive.ubuntu.com gutsy/universe Packages                                                                       
Hit http://archive.ubuntu.com gutsy/multiverse Packages                                                                     
Get:14 http://archive.ubuntu.com gutsy/main Sources [306kB]                                                                 
Get:15 http://archive.ubuntu.com gutsy/multiverse Sources [56.8kB]                                                          
Get:16 http://archive.ubuntu.com gutsy/restricted Sources [2120B]                                                           
Hit http://archive.ubuntu.com gutsy-updates/universe Packages                                                               
Hit http://archive.ubuntu.com gutsy-updates/main Packages                                                                   
Hit http://archive.ubuntu.com gutsy-updates/multiverse Packages                                                             
Hit http://archive.ubuntu.com gutsy-updates/restricted Packages                                                             
Get:17 http://archive.ubuntu.com gutsy-updates/universe Sources [8412B]                                                     
Get:18 http://archive.ubuntu.com gutsy-updates/main Sources [30.6kB]                                                        
Get:19 http://archive.ubuntu.com gutsy-updates/multiverse Sources [1702B]                                                   
Get:20 http://archive.ubuntu.com gutsy-updates/restricted Sources [937B]                                                    
Get:21 http://archive.ubuntu.com gutsy-proposed/universe Packages [31.2kB]                                                  
Get:22 http://archive.ubuntu.com gutsy-proposed/main Packages [103kB]                                                       
Get:23 http://archive.ubuntu.com gutsy-proposed/multiverse Packages [7569B]                                                 
Get:24 http://archive.ubuntu.com gutsy-proposed/restricted Packages [4263B]                                                 
Get:25 http://archive.ubuntu.com gutsy-proposed/universe Sources [5407B]                                                    
Get:26 http://archive.ubuntu.com gutsy-proposed/main Sources [27.9kB]                                                       
Get:27 http://archive.ubuntu.com gutsy-proposed/multiverse Sources [1190B]                                                  
Get:28 http://archive.ubuntu.com gutsy-proposed/restricted Sources [937B]                                                   
Get:29 http://archive.ubuntu.com gutsy-backports/universe Packages [65.3kB]                                                 
Get:30 http://archive.ubuntu.com gutsy-backports/main Packages [15.4kB]                                                     
Get:31 http://archive.ubuntu.com gutsy-backports/multiverse Packages [3175B]                                                
Get:32 http://archive.ubuntu.com gutsy-backports/restricted Packages [14B]                                                  
Get:33 http://archive.ubuntu.com gutsy-backports/universe Sources [13.3kB]                                                  
Get:34 http://archive.ubuntu.com gutsy-backports/main Sources [5991B]                                                       
Get:35 http://archive.ubuntu.com gutsy-backports/multiverse Sources [1626B]                                                 
Get:36 http://archive.ubuntu.com gutsy-backports/restricted Sources [14B]                                                   
Fetched 2039kB in 1m8s (29.6kB/s)                                                                                           
Reading package lists... Done


```

And of  cat /etc/apt/sources.list

```

# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe main multiverse restricted #Added by software-properties
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

Thanks

---

### Post by forestpixie on 2008-01-29
> **forestpixie said:**
> 
Edit - I don't actually know if kde-config is a pacakge - I can't find it either, I guess it'spart of kde, though why you can't install it I don't know. I'll have a look into it

Try ```
sudo apt-get install kdevelop
``` again and paste the whole error ?

---

### Post by bargi on 2008-01-29
I have run the command :

 sudo apt-get install kdevelop

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdebase-bin kdelibs4c2a libarts1c2a libaudio2 libavahi-qt3-1 libcvsservice0 libqt3-mt
Suggested packages:
  khelpcenter fam libqt3-mt-dev kdelibs4-dev sgmltools-lite gettext qt3-dev-tools ark kbabel kiconedit kdesdk-scripts
  graphviz kdebase-kio-plugins exuberant-ctags kdelibs4-doc qt3-doc konsole cmake ruby nas libqt3-mt-psql libqt3-mt-mysql
  libqt3-mt-odbc
Recommended packages:
  perl-suid kdevelop-doc libarts1-akode
The following NEW packages will be installed:
  kdebase-bin kdelibs4c2a kdevelop libarts1c2a libaudio2 libavahi-qt3-1 libcvsservice0 libqt3-mt
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.5kB/25.0MB of archives.
After unpacking 74.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]
Fetched 2109B in 8s (252B/s)         
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I don't know why there is this error ........

Should I install kde ??????

Thanks

---

### Post by forestpixie on 2008-01-29
where you have lines in your sources list like this # deb http - remove the # so it looks like this deb http

```
sudo cp /etc/apt/sources.list /etc/apt/sources.bak
```

```
gksudo gedit /etc/apt/sources.list
```

then update again with sudo apt-get update

---

### Post by bargi on 2008-01-29
Hi have remove the # sign and again run the command sudo apt-get upgrade.........

and after that  sudo apt-get install kdevelop..

But the same problem was there........

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kdebase-bin kdelibs4c2a libarts1c2a libaudio2 libavahi-qt3-1 libcvsservice0 libqt3-mt
Suggested packages:
  khelpcenter fam libqt3-mt-dev kdelibs4-dev sgmltools-lite gettext qt3-dev-tools ark kbabel kiconedit kdesdk-scripts
  graphviz kdebase-kio-plugins exuberant-ctags kdelibs4-doc qt3-doc konsole cmake ruby nas libqt3-mt-psql libqt3-mt-mysql
  libqt3-mt-odbc
Recommended packages:
  perl-suid kdevelop-doc libarts1-akode
The following NEW packages will be installed:
  kdebase-bin kdelibs4c2a kdevelop libarts1c2a libaudio2 libavahi-qt3-1 libcvsservice0 libqt3-mt
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 77.5kB/25.0MB of archives.
After unpacking 74.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]
Fetched 2112B in 8s (254B/s)            
Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/n/nas/libaudio2_1.9-2_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Thanks

---

### Post by Partyboi2 on 2008-01-29
try changing server, open Software Sources (for gnome System>admin>software sources) and change the server over to main from in.
then 
```
sudo apt-get update
``````
sudo apt-get install kdevelop
```

---

### Post by bargi on 2008-01-29
Problem Solved..........

Thanks to All of U :)

---

