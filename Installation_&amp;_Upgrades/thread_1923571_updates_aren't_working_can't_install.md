---
title: "updates aren't working can't install"
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by mlkirchgessner on 2012-02-10
i tried to install the huge amount of updates that are on this thing and it's not working.. i tried to apt-get a program called shutter also but that doesn't work. warning! I'm pretty new at this still!


After this operation, 54.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Selecting previously deselected package gnome-web-photo.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-3.0.0-15-generic-pae': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

just wanted to see if anybody could help me remedy this. 
thanks

---

### Post by cortman on 2012-02-10
> **mlkirchgessner said:**
> i tried to install the huge amount of updates that are on this thing and it's not working.. i tried to apt-get a program called shutter also but that doesn't work. warning! I'm pretty new at this still!


After this operation, 54.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Selecting previously deselected package gnome-web-photo.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-3.0.0-15-generic-pae': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

just wanted to see if anybody could help me remedy this. 
thanks

I'll ask you to run the classic "package problems diagnostic command"-

```
sudo apt-get update
```

and post the output here.

---

### Post by mlkirchgessner on 2012-02-11
just installed ubuntu and i can't install anything. this is what i get every time 

(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-3.0.0-15-generic-pae': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


anybody have this problem? or have any suggestions? thanks

---

### Post by mlkirchgessner on 2012-02-11
its fully installed 

everything seems to be running fine except the fact that i can't download and install anything 

i tried sudo apt-get install -f 

and 

sudo apt-get update


  	 	 	 	 	 	  # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted 
  
 # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to 
 # newer versions of the distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted 
  
 ## Major bug fix updates produced after the final release of the 
 ## distribution. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
 ## team. Also, please note that software in universe WILL NOT receive any 
 ## review or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe 
  
 ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
 ## team, and may not be under a free licence. Please satisfy yourself as to  
 ## your rights to use the software. Also, please note that software in  
 ## multiverse WILL NOT receive any review or updates from the Ubuntu 
 ## security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse 
  
 ## N.B. software from this repository may not have been tested as 
 ## extensively as that contained in the main release, although it includes 
 ## newer versions of some applications which may provide useful features. 
 ## Also, please note that software in backports WILL NOT receive any review 
 ## or updates from the Ubuntu security team. 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse 
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse 
  
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse 
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse 
  
 ## Uncomment the following two lines to add software from Canonical's 
 ## 'partner' repository. 
 ## This software is not part of Ubuntu, but is offered by Canonical and the 
 ## respective vendors as a service to Ubuntu users. 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner 
 deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner 
  
 ## This software is not part of Ubuntu, but is offered by third-party 
 ## developers who want to ship their latest software. 
 deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main 
 deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

---

### Post by josephmills on 2012-02-11
It looks like you might be getting hung uop on the kernel. could you please open your terminal and type in 
```
cat /etc/apt/sources.list
``` then paste here thanks

---

### Post by cortman on 2012-02-11
> **cortman said:**
> and post the output here.

Output???

---

### Post by josephmills on 2012-02-11
> **MrMeen said:**
> This is what im getting

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse





In terminal do this 
```
gksudo gedit /etc/apt/sources.list
```
and please make it look like this 
```

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse



```
Now proff read 2x then save it DONT FORGET TO SAVE IT 

then do a ```
sudo apt-get update && sudo apt-get -y upgrade 
``` 
let us know how it goes

---

### Post by mlkirchgessner on 2012-02-11
i just added it to the last post of mine i couldn't paste it any other way . im new at this so i probably just don't know how at any rate its up there thanks

---

### Post by josephmills on 2012-02-11
look up again I EDITED the last post that I posted

---

### Post by josephmills on 2012-02-11
> **MrMeen said:**
> This is what i get when i do the upgrade

```
Ign http://archive.ubuntu.com karmic Release.gpg
Ign http://archive.ubuntu.com karmic/main Translation-en_US
Ign http://archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic/universe Translation-en_US
Ign http://archive.ubuntu.com karmic/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic-updates Release.gpg
Ign http://archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com karmic Release   
Ign http://security.ubuntu.com karmic-security Release
Ign http://archive.ubuntu.com karmic-updates Release
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic/multiverse Packages
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://archive.ubuntu.com karmic/multiverse Sources
Ign http://archive.ubuntu.com karmic-updates/main Packages
Ign http://security.ubuntu.com karmic-security/multiverse Sources
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://archive.ubuntu.com karmic-updates/restricted Packages
Ign http://archive.ubuntu.com karmic-updates/main Sources
Ign http://archive.ubuntu.com karmic-updates/restricted Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Ign http://archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://archive.ubuntu.com karmic/main Packages
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://security.ubuntu.com karmic-security/restricted Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://archive.ubuntu.com karmic/restricted Packages
Ign http://archive.ubuntu.com karmic/main Sources
Ign http://archive.ubuntu.com karmic/restricted Sources
Ign http://archive.ubuntu.com karmic/universe Packages
Ign http://archive.ubuntu.com karmic/universe Sources
Ign http://archive.ubuntu.com karmic/multiverse Packages
Ign http://archive.ubuntu.com karmic/multiverse Sources
Ign http://archive.ubuntu.com karmic-updates/main Packages
Ign http://archive.ubuntu.com karmic-updates/restricted Packages
Ign http://security.ubuntu.com karmic-security/multiverse Sources
Err http://security.ubuntu.com karmic-security/main Packages
  404  Not Found [IP: 91.189.92.166 80]
Ign http://archive.ubuntu.com karmic-updates/main Sources
Ign http://archive.ubuntu.com karmic-updates/restricted Sources
Ign http://archive.ubuntu.com karmic-updates/universe Packages
Ign http://archive.ubuntu.com karmic-updates/universe Sources
Ign http://archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://archive.ubuntu.com karmic-updates/multiverse Sources
Err http://archive.ubuntu.com karmic/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com karmic-security/restricted Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/main Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/restricted Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/universe Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/universe Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://archive.ubuntu.com karmic/universe Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/universe Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/multiverse Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic/multiverse Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/main Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/restricted Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/main Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/restricted Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://security.ubuntu.com karmic-security/multiverse Packages
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com karmic-security/multiverse Sources
  404  Not Found [IP: 91.189.92.166 80]
Err http://archive.ubuntu.com karmic-updates/universe Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/universe Sources
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/multiverse Packages
  404  Not Found [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com karmic-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.31 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.88.31 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ 

```


Would the fact that im using a live usb be the problem. if so how do i get around it. thanks for the help so far


ok if you like to use the command line use nano or vi. but as far as what is going on please open that list up and put a # in front of the ones that you can not connect to. then try again.

---

### Post by mlkirchgessner on 2012-02-11
yo linux guru you got any input on my problem

---

### Post by mlkirchgessner on 2012-02-11
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages                   
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [1,384 B]                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex                  
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [1,818 B]                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Fetched 13.0 kB in 2s (5,609 B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
noi5eb0x@noi5eb0x-Satellite-L675D:~$ sudo apt-get update 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg       
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Reading package lists... Done
noi5eb0x@noi5eb0x-Satellite-L675D:~$ sudo apt-get -install shutter
E: Command line option 'i' [from -install] is not known.
noi5eb0x@noi5eb0x-Satellite-L675D:~$ sudo apt-get install shutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-web-photo imagemagick libart-2.0-2 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcdt4 libencode-locale-perl libextutils-depends-perl
  libextutils-pkgconfig-perl libfile-homedir-perl libfile-listing-perl libfile-which-perl libfont-afm-perl libglade2-0 libgnome2-0 libgnome2-canvas-perl libgnome2-gconf-perl
  libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-extra libgoo-canvas-perl
  libgoocanvas-common libgoocanvas3 libgraph4 libgtk2-imageview-perl libgtk2-unique-perl libgtkimageview0 libgvc5 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhttp-server-simple-perl
  libilmbase6 libio-socket-ssl-perl liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore3 libmagickcore3-extra libmagickwand3 libmailtools-perl
  libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libnetpbm10 libopenexr6 libpathplan4 libproc-processtable-perl libproc-simple-perl libsort-naturally-perl
  libtie-ixhash-perl libtimedate-perl liburi-perl libwww-mechanize-perl libwww-perl libwww-robotrules-perl libx11-protocol-perl libxml-namespacesupport-perl libxml-parser-perl
  libxml-sax-expat-perl libxml-sax-perl libxml-simple-perl libxml-twig-perl libxml-xpath-perl netpbm perlmagick
Suggested packages:
  imagemagick-doc autotrace curl enscript ffmpeg gimp gnuplot grads hp2xx html2ps libwmf-bin mplayer povray radiance texlive-base-bin transfig ufraw-batch libbonobo2-bin
  libdata-dump-perl libio-socket-inet6-perl libcrypt-ssleay-perl libauthen-ntlm-perl libunicode-map8-perl libunicode-string-perl xml-twig-tools libnet-dbus-glib-perl
The following NEW packages will be installed:
  gnome-web-photo imagemagick libart-2.0-2 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcdt4 libencode-locale-perl libextutils-depends-perl
  libextutils-pkgconfig-perl libfile-homedir-perl libfile-listing-perl libfile-which-perl libfont-afm-perl libglade2-0 libgnome2-0 libgnome2-canvas-perl libgnome2-gconf-perl
  libgnome2-perl libgnome2-vfs-perl libgnome2-wnck-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-extra libgoo-canvas-perl
  libgoocanvas-common libgoocanvas3 libgraph4 libgtk2-imageview-perl libgtk2-unique-perl libgtkimageview0 libgvc5 libhtml-form-perl libhtml-format-perl libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libhttp-server-simple-perl
  libilmbase6 libio-socket-ssl-perl liblqr-1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmagickcore3 libmagickcore3-extra libmagickwand3 libmailtools-perl
  libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libnetpbm10 libopenexr6 libpathplan4 libproc-processtable-perl libproc-simple-perl libsort-naturally-perl
  libtie-ixhash-perl libtimedate-perl liburi-perl libwww-mechanize-perl libwww-perl libwww-robotrules-perl libx11-protocol-perl libxml-namespacesupport-perl libxml-parser-perl
  libxml-sax-expat-perl libxml-sax-perl libxml-simple-perl libxml-twig-perl libxml-xpath-perl netpbm perlmagick shutter
0 upgraded, 81 newly installed, 0 to remove and 325 not upgraded.
Need to get 0 B/12.6 MB of archives.
After this operation, 54.0 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Selecting previously deselected package gnome-web-photo.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-image-3.0.0-15-generic-pae': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
noi5eb0x@noi5eb0x-Satellite-L675D:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                                                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Reading package lists... Done

---

### Post by cortman on 2012-02-11
As Josephmills said-

a) it looks like the kernel is making problems. Installing a different kernel version may fix it.
b) Please don't post multiple threads on the same subject. It sounds like other (more knowledgable) help is being given there.

---

### Post by savanna on 2012-02-11
Sounds like your upgrade failed. Run:

sudo apt-get update
sudo aptitude safe-upgrade

---

### Post by oldos2er on 2012-02-12
Threads merged. Please only open one thread per topic/question.

---

