---
title: "Fresh Install - Problems trying to install new software"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by Ausmosis on 2008-01-16
G'day

I have just completed a fresh install (Gutsy 7.10) but having problems installing 3rd party applications. For example when trying to install vlc, I get the following errors:

vlc:
 Depends: vlc-nox but it is not going to be installed
 Depends: libsdl-image1.2 (>=1.2.5) but it is not installable
 Depends: ttf-dejavu  but it is not installable

This is happening with other applications as well with different dependencies which has me completely stumped. The reason being is that I did  fresh install on another identical PC last week and everything went to plan and I have no dependency issues what-so-ever. I even compared source lists and both are the same. Is anyone else having this issue at the moment?

I should mention that both PC do have different graphic cards. The one I have no issues with has a GForce4 and the new install PC has a GForce2. Not sure if this may be the cause of my problems??

Cheers

---

### Post by jeffus_il on 2008-01-16
Have a good look at your repositories in Synaptic, Settings>Repositories and do a reload.

---

### Post by Ausmosis on 2008-01-16
> **jeffus_il said:**
> Have a good look at your repositories in Synaptic, Settings>Repositories and do a reload.

jeffus_il: I tried reloading the repositories a number of times but it's still doing the same thing.

---

### Post by jeffus_il on 2008-01-16
Oh, you are installing vlc as 3rd party, it's also in the repository, if you have made changes to the 3rd party repositories, remove them and see it your problem disappears, If so, add the changes one by one to see which one causes the problem, If you can't do it thru the repository, consider downloading a ".deb" package and installing using "gdebi"

---

### Post by Ausmosis on 2008-01-16
removed the 3rd party repos and still getting the same messages. I have even tried other applications and I'm getting similar problems. It can't seem to resolve the dependency requirements.

For example I get the following when trying to install nvidia-legacy-kernel-source:

nvidia-legacy-kernel-source:
 Depends: debhelper (>4.0.0) but it is not installable
 Depends: dpatch (>=2.0.0) but it is not installable

I'm really stumped over this especially considering I had no issues last week with the other PC!

---

### Post by Partyboi2 on 2008-01-16
what happens when you
```
 sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by Ausmosis on 2008-01-16
And here is another just to show that I'm not going crazy! :)

xmms:
 Depends: libmikmod2 (>=3.1.10) but it is not installable

---

### Post by Ausmosis on 2008-01-16
> **Partyboi2 said:**
> what happens when you
```
 sudo apt-get update
``````
sudo apt-get upgrade
```

Partyboi2: Here is the output from both:

```

 sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Get:1 http://mirror.internode.on.net gutsy-updates Release.gpg [191B]
Ign http://mirror.internode.on.net gutsy-updates/universe Translation-en_AU
Ign http://mirror.internode.on.net gutsy-updates/multiverse Translation-en_AU
Get:2 http://mirror.internode.on.net gutsy Release.gpg [191B]
Ign http://mirror.internode.on.net gutsy/universe Translation-en_AU
Ign http://mirror.internode.on.net gutsy/multiverse Translation-en_AU
Get:3 http://mirror.internode.on.net gutsy-security Release.gpg [191B]
Ign http://mirror.internode.on.net gutsy-security/main Translation-en_AU
Ign http://mirror.internode.on.net gutsy-security/restricted Translation-en_AU
Ign http://mirror.internode.on.net gutsy-security/universe Translation-en_AU
Ign http://mirror.internode.on.net gutsy-security/multiverse Translation-en_AU 
Hit http://mirror.internode.on.net gutsy-updates Release                       
Hit http://mirror.internode.on.net gutsy Release                               
Hit http://mirror.internode.on.net gutsy-security Release                      
Hit http://mirror.internode.on.net gutsy-updates/main Sources                  
Hit http://mirror.internode.on.net gutsy-updates/restricted Sources            
Hit http://mirror.internode.on.net gutsy-updates/universe Packages             
Hit http://mirror.internode.on.net gutsy-updates/universe Sources              
Hit http://mirror.internode.on.net gutsy-updates/multiverse Packages           
Hit http://mirror.internode.on.net gutsy-updates/multiverse Sources            
Hit http://mirror.internode.on.net gutsy/universe Packages                     
Hit http://mirror.internode.on.net gutsy/universe Sources                      
Hit http://mirror.internode.on.net gutsy/multiverse Packages                   
Hit http://mirror.internode.on.net gutsy/multiverse Sources                    
Hit http://mirror.internode.on.net gutsy-security/main Packages                
Hit http://mirror.internode.on.net gutsy-security/restricted Packages          
Hit http://mirror.internode.on.net gutsy-security/main Sources                 
Hit http://mirror.internode.on.net gutsy-security/restricted Sources           
Hit http://mirror.internode.on.net gutsy-security/universe Packages            
Hit http://mirror.internode.on.net gutsy-security/universe Sources             
Hit http://mirror.internode.on.net gutsy-security/multiverse Packages          
Hit http://mirror.internode.on.net gutsy-security/multiverse Sources           
Fetched 3B in 16s (0B/s)                                                       
Reading package lists... Done
```

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by svenhenrik on 2008-01-16
I'm actually trying to help a friend with the exact same problem, new 7.10 install and he can't install any software.

The thing the two of you seem to have in common is that you lack gutsy/main in you sources.list, he only has:

deb [http://.../ubuntu](http://.../ubuntu) gutsy universe

How does your /etc/apt/sources.list look?

---

### Post by Ausmosis on 2008-01-16
> **svenhenrik said:**
> I'm actually trying to help a friend with the exact same problem, new 7.10 install and he can't install any software.

The thing the two of you seem to have in common is that you lack gutsy/main in you sources.list, he only has:

deb [http://.../ubuntu](http://.../ubuntu) gutsy universe

How does your /etc/apt/sources.list look?

svenhenrik: this is my source.list

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy multiverse
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security main restricted
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security main restricted
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security universe
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security universe
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security multiverse
deb-src http://mirror.internode.on.net/pub/ubuntu/ubuntu/ gutsy-security multiverse
# deb http://packages.medibuntu.org/ gutsy free
```

---

### Post by Ausmosis on 2008-01-16
svenhenrik: You were right!!... I added gutsy main to my source.list and ran apt-get update again. I got a few errors and it asked me to update again which I did and now everything is sweet. Thanks heaps for the pointer!! :)

---

