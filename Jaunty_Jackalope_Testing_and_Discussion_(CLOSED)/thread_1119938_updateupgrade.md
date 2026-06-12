---
title: "update/upgrade"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Insane_Homer on 2009-04-08
Hi there,

today I got this when doing a sudo apt-get update 

```
Err http://security.ubuntu.com jaunty-security-i386/main Packages
  404 Not Found
Hit http://gb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://gb.archive.ubuntu.com jaunty-updates-i386/main Packages
Ign http://gb.archive.ubuntu.com jaunty-updates-i386/restricted Packages
Ign http://gb.archive.ubuntu.com jaunty-updates-i386/universe Packages
Err http://security.ubuntu.com jaunty-security-i386/restricted Packages
  404 Not Found
Ign http://gb.archive.ubuntu.com jaunty-updates-i386/multiverse Packages
Err http://gb.archive.ubuntu.com jaunty-i386/main Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-i386/restricted Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-i386/universe Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-i386/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security-i386/universe Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security-i386/multiverse Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/main Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/restricted Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/universe Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/multiverse Packages
  404 Not Found
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

if open and use the update manager it tells me a require a partial upgrade and that 3 apps to be removed and 5 added and 2 upgraded. Each app then generates a failure and crashes out?

apt.log
```
Log time: 2009-04-08 18:45:57.117935
Installing libopal3.6.1 as dep of ekiga
Installing libpt2.6.1 as dep of libopal3.6.1
Installing libpt2.6.1-plugins-alsa as dep of ekiga
Installing libpt2.6.1-plugins-v4l2 as dep of ekiga
Installing libindicate1 as dep of indicator-applet
Starting
Starting 2
Investigating libopal3.6.1
Package libopal3.6.1 has broken dep on libopal3.4.2
  Considering libopal3.4.2 -1 as a solution to libopal3.6.1 0
  Added libopal3.4.2 to the remove list
  Fixing libopal3.6.1 via remove of libopal3.4.2
Investigating libpt2.6.1-plugins-alsa
Package libpt2.6.1-plugins-alsa has broken dep on libpt2.4.2-plugins-alsa
  Considering libpt2.4.2-plugins-alsa -1 as a solution to libpt2.6.1-plugins-alsa 0
  Added libpt2.4.2-plugins-alsa to the remove list
  Fixing libpt2.6.1-plugins-alsa via remove of libpt2.4.2-plugins-alsa
Investigating libpt2.6.1-plugins-v4l2
Package libpt2.6.1-plugins-v4l2 has broken dep on libpt2.4.2-plugins-v4l2
  Considering libpt2.4.2-plugins-v4l2 -1 as a solution to libpt2.6.1-plugins-v4l2 0
  Added libpt2.4.2-plugins-v4l2 to the remove list
  Fixing libpt2.6.1-plugins-v4l2 via remove of libpt2.4.2-plugins-v4l2
Done
ERROR:root:NvidiaDetection returned a error: dir ./modaliases/ not found
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'
```

any attempts to run it a second time results in update manager closing without error or warning?

a sudo apt-get dist upgrade appears to perform the upgrade.

I changed the sources from GB (UK) to Main.

```
Err http://gb.archive.ubuntu.com jaunty-i386/universe Packages       
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-i386/multiverse Packages     
  404 Not Found
Err http://security.ubuntu.com jaunty-security-i386/universe Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/main Packages   
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/restricted Packages
  404 Not Found
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages    
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources     
Err http://gb.archive.ubuntu.com jaunty-updates-i386/universe Packages
  404 Not Found
Err http://gb.archive.ubuntu.com jaunty-updates-i386/multiverse Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security-i386/multiverse Packages
  404 Not Found
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by BlackNinjaVirus on 2009-04-08
Only available options for that site:

jaunty-backports 	 
jaunty-proposed	 
jaunty-security 	 
jaunty-updates	 
jaunty

---

### Post by nystire on 2009-04-09
Try using the main repository, perhaps?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) explains how to change this setting.

---

### Post by Insane_Homer on 2009-04-09
> **nystire said:**
> Try using the main repository, perhaps?

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) explains how to change this setting.


I tried that and still for the same result, still seems to want to download from the gb- locations regardless.

Looking at the etc/apt/sources.list timestamp the file is being updated according to the timestamp but the gb-entries remain.

seems like the sources.list is not updating with the changes.

Wondering if this is a symptom of ext4 write delay?

---

### Post by nystire on 2009-04-09
MAKE A BACKUP COPY OF THE sources.list FILE!
Then try editing the sources.list file and removing the 'gb.' from the start of each line. Then rerun the 'sudo apt-get update' command.

---

### Post by Insane_Homer on 2009-04-14
> **nystire said:**
> MAKE A BACKUP COPY OF THE sources.list FILE!
Then try editing the sources.list file and removing the 'gb.' from the start of each line. Then rerun the 'sudo apt-get update' command.

did this today finally (been down with manflu for the past 10 days)

Still getting...

```
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Err http://security.ubuntu.com jaunty-security-i386/main Packages
  404 Not Found
Err http://security.ubuntu.com jaunty-security-i386/restricted Packages
  404 Not Found
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Err http://security.ubuntu.com jaunty-security-i386/universe Packages
  404 Not Found
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://archive.ubuntu.com jaunty-updates-i386/main Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/universe Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/main Packages
Err http://security.ubuntu.com jaunty-security-i386/multiverse Packages
  404 Not Found
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://archive.ubuntu.com jaunty-i386/main Packages
Ign http://archive.ubuntu.com jaunty-i386/restricted Packages
Ign http://archive.ubuntu.com jaunty-i386/universe Packages
Ign http://archive.ubuntu.com jaunty-i386/multiverse Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/main Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/restricted Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/universe Packages
Ign http://archive.ubuntu.com jaunty-updates-i386/multiverse Packages
Err http://archive.ubuntu.com jaunty-i386/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-i386/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-i386/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-i386/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-updates-i386/main Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-updates-i386/restricted Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-updates-i386/universe Packages
  404 Not Found [IP: 91.189.88.46 80]
Err http://archive.ubuntu.com jaunty-updates-i386/multiverse Packages
  404 Not Found [IP: 91.189.88.46 80]
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/main/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/restricted/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/universe/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/jaunty-security-i386/multiverse/binary-amd64/Packages  404 Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/restricted/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/universe/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates-i386/multiverse/binary-amd64/Packages  404 Not Found [IP: 91.189.88.46 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Sources.list (x64)
```
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse


### ia32-apt-get entries ###

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta amd64 (20090324)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ jaunty-i386 main restricted

## Major bug fix updates produced after the final release of the
## distribution.  
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates-i386 main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ jaunty-i386 universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates-i386 universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team. 
deb http://archive.ubuntu.com/ubuntu/ jaunty-i386 multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates-i386 multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.  
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. 
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security-i386 main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security-i386 universe
deb http://security.ubuntu.com/ubuntu jaunty-security-i386 multiverse
```

---

### Post by amazing mustard on 2009-04-14
i get sort of the same thing. when checking for updates in the manager i get:

> Failed to fetch [http://www.backports.org/debian/dists/stable/ucf/binary-amd64/Packages.gz](http://www.backports.org/debian/dists/stable/ucf/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://people.debian.org/~dexter/dists/php5/woody/binary-amd64/Packages.gz](http://people.debian.org/~dexter/dists/php5/woody/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [http://people.debian.org/~dexter/dists/php5/woody/source/Sources.gz](http://people.debian.org/~dexter/dists/php5/woody/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.


packages are not present at the repository sites and not anywhere else (that i could find). also, nobody seems to get the same error on these packages i get.

---

### Post by crjackson on 2009-04-14
> **amazing mustard said:**
> i get sort of the same thing. when checking for updates in the manager i get:



packages are not present at the repository sites and not anywhere else (that i could find). also, nobody seems to get the same error on these packages i get.

Are you using any DNS mangement services? It seems like something is blocking the connection.

EDIT: After checking here from work, the addresses for ~dexter don't seem to be valid right now.

---

### Post by amazing mustard on 2009-04-14
it hasn't been valid for weeks or even months. is another repository available or are my packages EOL?

---

### Post by crjackson on 2009-04-14
> **amazing mustard said:**
> it hasn't been valid for weeks or even months. is another repository available or are my packages EOL?

What packages does this repo service?

---

### Post by Insane_Homer on 2009-04-20
I'm still getting the same errors

can anyone post a standard copy of their **sources.list** x64 edition from Main or localised European so I can overwrite mine.

From what I see the error says...

```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/***[COLOR="Red"]jaunty-updates-i386[/COLOR]***/main/binary-amd64/Packages  404 Not Found [IP: 91.189.88.45 80]

```

But if I browse those http paths it appears it should be 

```
http://archive.ubuntu.com/ubuntu/dists/***[COLOR="Red"]jaunty-updates[/COLOR]***/multiverse/binary-amd64/
```

So how do I fix that?

---

