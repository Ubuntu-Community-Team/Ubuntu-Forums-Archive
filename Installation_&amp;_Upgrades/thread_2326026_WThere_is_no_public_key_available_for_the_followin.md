---
title: "W:There is no public key available for the following - Help"
date: 2016-05-27
forum: Installation &amp; Upgrades
---

### Post by IslingtonN5 on 2016-05-27
I hope the Ubuntu forum can help.
"Note: I don't want to upgrade to Ubuntu 16.04 LTS as i got the black screen when updating another laptop and that was pure hell to resolve.

I get the below message when i try updating using the Software & Updates application, does anyone know how i can resolve this?  

The output from the Software & Updates application is:

W:There is no public key available for the following key IDs:
1397BC53640DB551, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed fil
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/multiverse/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::14 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/restricted/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::14 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/universe/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::14 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic-proposed/main/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::14 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/utopic/main/source/Sources)  404  Not Found [IP: 2001:67c:1560:8001::14 80]

---

### Post by howefield on 2016-05-27
Opening Software and Updates should allow you to uncheck the repositories that are causing you the errors, including the cdrom that it is looking for.

Google has dropped support for the 32 bit version of chrome so you can remove that repository.

What version of Ubuntu are you running, Utopic is long since end of life, hence the errors with those repositories.

Posting the output of 

```
cat /etc/lsb-release
```

and

```
cat /etc/apt/sources.list
``` 

might help.

---

### Post by Geoffrey_Arndt on 2016-05-27
Make sure you only have the default sources in your "sources list" . . . in Software & Updates>Other . . . untick cdrom as a source, and untick any PPA's (if you have those).   Close the sources window and you can reload the updated package list.   You might also run a server check (on first tab - download from - other - find best server).

---

### Post by IslingtonN5 on 2016-05-28
Thank you both.

I tried un-ticking "cdrom as a source + PPA's but sadly it did not work.


Here is the output from "cat /etc/lsb-release" and "cat /etc/apt/sources.list".
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.10
DISTRIB_CODENAME=utopic
DISTRIB_DESCRIPTION="Ubuntu 14.10"


```
bob@Bob:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic main universe restricted multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-updates main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-updates main universe restricted multiverse #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-backports main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-backports main universe restricted multiverse #Added by software-properties

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-security main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-security main universe restricted multiverse #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-proposed main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) utopic-proposed main universe restricted multiverse #Added by software-properties
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
```

---

### Post by Bashing-om on 2016-05-28
IslingtonN5; Yuk !

> 
DISTRIB_DESCRIPTION="Ubuntu 14.10"

Release 14.10 is indeed End_Of_Life and as such no longer has support. The software repository no longer exists.
A long hard road to upgrade the current 14.10 to a current release, though it can be done:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
14.10 -> 15.04 (EOL) -> 15.10 -> 16.04

Will be the faster and greater confidence to do a clean fresh install of 16.04 in the flavor of your choice .

[INDENT][INDENT]that is
[INDENT][INDENT]the state of the affair
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Philip Gray on 2016-06-24
Good evening IslingtonN5


This evening I encountered the same issue you are having when I did an update in my Mint 17.3. It was caused by Google Chrome. I found a solution on another Ubuntu Forum. This solution worked for me. Try it and see if it works for you. They suggested this entry:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys [I]1397BC53640DB551

[/I]Where the number in italics is the number in the error message (my error number). I received this error
W: There is no public key available for the following key IDs: 1397BC53640DB551
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551


Regards
Philip

---

