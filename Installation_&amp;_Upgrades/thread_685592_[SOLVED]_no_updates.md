---
title: "[SOLVED] no updates"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by matthiayer on 2008-02-02
hi,

i used a recovery cd to reinstall windows xp in another partition for games, and formatted my hole drive!

so now i'm reinstalling gutsy, so i have a fresh install
when i open the update-manager, it says there are no updates!!
but i know i should have tons of updates!

and now i want to install avant window navigator, and it wont install because of the update problem!!

does anyone have an idea of what i can do?

---

### Post by taurus on 2008-02-02
Make sure you have all the repos available in /etc/apt/sources.list.

System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and make sure there is a check mark on all the lines except the last one, Source code, and the Cdrom in the window below.  Save it.  Then, close synaptic and run these two commands from a terminal.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by erdomi on 2008-02-02
I have the same problem of not seeing any upgrades.  But I've added some repos and I'm not sure just checking all but the last repository in Synaptic applies to me.  Exactly which repositories are necessary for the upgrade?

Thanks!

---

### Post by taurus on 2008-02-02
> **erdomi said:**
> I have the same problem of not seeing any upgrades.  But I've added some repos and I'm not sure just checking all but the last repository in Synaptic applies to me.  Exactly which repositories are necessary for the upgrade?

Thanks!

Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by erdomi on 2008-02-02
Here it is:


[PHP]deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe


# deb http://archive.canonical.com/ubuntu dapper-commercial main

# deb http://www.mpe.mpg.de/~ach/kubuntu/dapper ./
# deb-src http://www.mpe.mpg.de/~ach/kubuntu/dapper ./[/PHP]

---

### Post by taurus on 2008-02-02
I would edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the # in front of all these repos (everything except the last two).

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.canonical.com/ubuntu dapper-commercial main

```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by matthiayer on 2008-02-02
thanks for the fast reply!!

but it still didn't work.
no errors, but no updates either, 
is it possible that it updated without me knowing it? (windows style?)
and is it possible to check the updates that are done in the past?

IT WORKED!!!
thanks 
but is iet safe and all?

---

### Post by erdomi on 2008-02-02
Thanks, Taurus.  I uncommented those lines and ran apt-get update.  That seemed to be fine.  Then I checked my updates (in the update manager) again and I got this error:


> The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Is it OK if those repositories are ignored?

I'm a little scared to do the apt-get upgrade because it is not recommended in the ubuntu documentation.

Thanks for you help.

-erdomi

---

### Post by jatiesch on 2008-02-02
hi i have a similar problem in using update manager and add/remove...
i have added a snapshot...
plz help...

---

