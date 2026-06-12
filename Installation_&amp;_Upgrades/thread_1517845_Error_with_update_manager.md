---
title: "Error with update manager"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by studysession on 2010-06-25
I am having a problem with the update manager in Ubuntu 10.04. When I check for new updates the "downloading package information" bar gets stuck on package 50 and I then get this error.

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release: The following signatures were invalid: NODATA 1 NODATA 2Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/binary-i386/Packages.bz2](http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/binary-i386/Packages.bz2)  Sub-process /bin/bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead.

It seems to have something to do with Cairo dock which I no longer have installed. Does anyone know how to stop this error?

---

### Post by Don Barzini on 2010-06-25
It looks like you used it when you were using Intrepid.

In a terminal type **cat /etc/apt/sources.list** and post the output.

It might be as simple as just commenting out that old repository.

---

### Post by studysession on 2010-06-25
Here you go

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) intrepid cairo-dock

---

### Post by Don Barzini on 2010-06-25
Edit the file **/etc/apt/sources.list** and comment out that repository put putting a **#** in front of that entry...

```
#deb http://repository.cairo-dock.org/ubuntu  intrepid cairo-dock
```

You could also delete the line if you want to.

After you are done editing... in a terminal run...

```
sudo apt-get update
```

---

### Post by studysession on 2010-06-25
Where can I find the sources file?

---

### Post by Don Barzini on 2010-06-25
> **studysession said:**
> Where can I find the sources file?

It is **/etc/apt/sources.list**.

To edit... in a terminal type...

```
gksudo gedit /etc/apt/sources.list
```

Do your edit... save the file... then run **sudo apt-get update** in the terminal.

```
sudo apt-get update
```

---

### Post by studysession on 2010-06-25
Ha, sorry I'm quite the newbie with Ubuntu. I deleted the line and the update works flawlessly again. Thanks so much for your help. :D

---

