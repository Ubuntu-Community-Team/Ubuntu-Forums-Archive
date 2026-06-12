---
title: "Can't upgrade from 7.04 to 7.10 because it failed to fetch!"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by yamilv on 2007-12-22
Hey everybody, I've been wanting to upgrade from 7.04 to 7.10 and I've been met with the following error message:
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. 
http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release.gpg: Could not resolve 'archive.ubuntustudio.org'
http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/i18n/Translation-en_US.bz2: Could not resolve 'archive.ubuntustudio.org'
http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/main/binary-i386/Packages.gz: Could not resolve 'archive.ubuntustudio.org'

```

How would I go about fixing this problem? Thank you!

---

### Post by Pumalite on 2007-12-22
I might be wrong, but I don't think there is an UbuntuStudio 7.10

---

### Post by taurus on 2007-12-22
You need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of all the 3rd party repos, the ones that you added in.  Save it and then see if you can upgrade to Gutsy now.

If not sure, just post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by Pumalite on 2007-12-22
We keep on learning.

---

### Post by Pumalite on 2007-12-22
Now that I know that, I could offer you to try this:
sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by yamilv on 2007-12-22
```
# 
# deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main

deb cdrom:[Ubuntu Studio 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# The Ubuntu Studio Repository

deb http://archive.ubuntustudio.org/ubuntustudio feisty main

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

---

### Post by taurus on 2007-12-22
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of these lines.

```

#deb http://archive.ubuntustudio.org/ubuntustudio feisty main


#deb http://download.tuxfamily.org/3v1deb feisty eyecandy
#deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```
Save it and close gedit window.  Then run

```
sudo apt-get update
```
Now, see if you can upgrade to Gutsy this time.

---

### Post by yamilv on 2007-12-22
Thank you for your help in regards to upgrading but upon completion and reboot, I can't even start ubuntu anymore. It tells me to use a different "greeter application", what exactly does that mean?

---

### Post by Deadmode on 2008-01-05
> **taurus said:**
> Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of these lines.

```

#deb http://archive.ubuntustudio.org/ubuntustudio feisty main


#deb http://download.tuxfamily.org/3v1deb feisty eyecandy
#deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```
Save it and close gedit window.  Then run

```
sudo apt-get update
```
Now, see if you can upgrade to Gutsy this time.

Does this file become obsolete after the upgrade? or is it important to un # what we have #'d?

---

### Post by Richard_2007 on 2008-01-28
ok I did the update manager install and it fails and now tried the above instructions and I get this!!!

sudo apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg                     
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
  Could not resolve 'security.ubuntu.com'
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages             
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources                    
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources              
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages             
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
  Could not resolve 'security.ubuntu.com'
Fetched 2B in 8s (0B/s)                                                        
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/edgy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/source/Sources.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Any ideas??

---

### Post by Partyboi2 on 2008-01-28
Open up your sources.lst and remove anything related to edgy.
```
gksudo gedit /etc/apt/sources.list
```
You should only have feisty. then 
```
sudo apt-get update
```

---

### Post by Richard_2007 on 2008-02-15
Ok finally on Gutsy haven't yet reinstalled ubuntustudio. Had ISP problems and suspect part of issue with installs were old files ie feisty files present. Once I erased the root and swap before formating the partitions and installed off a gutsy disk all went well, except of course wireless but that par for the course.

Otherwise gutsy is running fine so far.

Thanks for all your help!!

Richard:guitar:

---

