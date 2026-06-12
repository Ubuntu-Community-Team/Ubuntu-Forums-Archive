---
title: "Help : Can't update ubuntu 11.10"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by Docmero on 2012-05-02
[CENTER]Hi
I'm a new ubuntu user , I 've working on the system for few days now and it was fine
apart from an internt problem that I got fixed .
.............................................................................................................
I'm trying to update ubuntu 11.10 ( I don't want to upgrade it to 12.04)
Every time I try to check for update I get this error
Please check your internet connection , [B][I][U]though the internet connection is fine
and I'm using it now !![/U][/I][/B]
details :
```
W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```I tried _**sudo apt-get update**_ from terminal and I get the same error
> W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead._**gedit /etc/apt/sources.list**_
> # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restrictedI'm a complete noob , so please give me the solution in the very fine details , lol .
Thanks guys
[/CENTER]

---

### Post by jonizen on 2012-05-02
Hi,
Since im using ubuntu server im not sure if this is a solution cuz i cant test it myself, but this may be a sulotion.

[http://ubuntuforums.org/showthread.php?t=1904770](http://ubuntuforums.org/showthread.php?t=1904770)

i forgot, you can also find the new paths for the packages and just edit the paths manualy by do a "sudo vi /etc/apt/sources.list" or gedit if you like it "sudo gedit /etc/apt/sources.list" and just replace the paths.

But i made the guess that u already done the "sudo apt-get update" ? This to get the packages in the sourcelist.

---

### Post by plucky on 2012-05-02
> W: Failed to fetch [http://ppa.launchpad.net/sevenmachin...source/Sources](http://ppa.launchpad.net/sevenmachin...source/Sources) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachin...amd64/Packages](http://ppa.launchpad.net/sevenmachin...amd64/Packages) 404 Not Found

W: Failed to fetch [http://ppa.launchpad.net/sevenmachin...-i386/Packages](http://ppa.launchpad.net/sevenmachin...-i386/Packages) 404 Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead. 
That is because the PPA you are trying to access no longer appears to be available.

[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)

See [Index of Sevenmachines PPA](http://ppa.launchpad.net/sevenmachines/)

Open Software Sources through the **Settings** button in Update Manager and delete/disable the PPAs that are giving you the problem under the "Other Software" Tag.

Good luck

---

### Post by TBABill on 2012-05-02
> **plucky said:**
> That is because the PPA you are trying to access no longer appears to be available.
 
[http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/oneiric/main/source/Sources)
 
See [Index of Sevenmachines PPA]("http://ppa.launchpad.net/sevenmachines/")
 
Open Software Sources through the **Settings** button in Update Manager and delete/disable the PPAs that are giving you the problem under the "Other Software" Tag.
 
Good luck
 +1
 
You can also open the sources.list file like you did, but as root, and comment out the PPA (using # just like the first listings for the CD).

---

### Post by Docmero on 2012-05-03
Thanks guys I've unchecked them from Update Settings and the problem is gone now :)

---

