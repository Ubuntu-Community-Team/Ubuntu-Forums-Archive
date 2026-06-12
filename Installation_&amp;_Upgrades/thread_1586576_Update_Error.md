---
title: "Update Error"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by ViKz on 2010-10-02
Hey, I'm hoping someone is able to help. I'm a complete novice with Linux OS but from what I've seen of it so far (only had it for a couple of weeks), I'm impressed. Although, I keep getting the following errors when Ubuntu attempts to update:

```

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://repository.glx-dock.org lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://packages.medibuntu.org/dists/lucid/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://repository.glx-dock.org/ubuntu/dists/lucid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```I have tried searching for a solution to the errors but I can't seem to find anything. I'm not sure whether this will help but I'm using Ubuntu 10.04

---

### Post by stee1rat on 2010-10-02
It says that it can't reach the repositories mentioned in the message. Is there any problem with your internet connection or a firewall? 'Cause this repos looks available for me.

In any way you can delete or comment this repos in /etc/apt/sources.list or through system - administartion - software sources.

---

### Post by ViKz on 2010-10-02
Thanks for the quick response. I haven't any problems with my internet or firewall...I'm using Firefox to access the Internet. Forgive me for sounding like a novice but how do I delete repositories?

---

### Post by clairejaffa on 2010-10-04
i have the same problem-almost identical.keeps asking for the 10.10 beta disc only i never had one as i just upgraded.i have downloaded 10.10 release candidate but that doesn't help.
i know i should of waited till 10 Oct for the release version but to late now :)

any help would be great thanks.:P

---

### Post by phoenix1/4 on 2010-10-06
Vikz, Im having similar troubles. Im trying to update through a proxy server, and Im getting the same error as you. I know this is a problem on my side (I have used these repos before through this proxy) and it refuses to work. I've tried different repo settings, perhaps it is due to my network settings? Any help on this would be great!

---

### Post by sikander3786 on 2010-10-07
Disbale any third party repositories from System > Administration > Software. It should be under the Other Software tab I think.

Also try changing the update servers from System > Administration > Software Sources, select the Main Server preferably and then,

```
sudo apt-get update
```

If it still doesn't work, post the output of

```
cat /etc/apt/sources.list
```

---

### Post by phoenix1/4 on 2010-10-07
Hi, thanks for the reply, output of sources.list is:
```

# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# deb-src http://archive.ubuntu.com/ubuntu lucid main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu lucid main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu lucid-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu lucid universe
deb http://archive.ubuntu.com/ubuntu lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu lucid multiverse
deb http://archive.ubuntu.com/ubuntu lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu lucid-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu lucid-security universe
deb http://archive.ubuntu.com/ubuntu lucid-security multiverse
```

/etc/apt/sources.list.d is an empty directory.

Thanks!

---

### Post by sikander3786 on 2010-10-07
Your sources.list seems fine. Did you try switching the update servers as mentioned above?

```
sudo apt-get update
```

What is the output after changing the update server?

---

### Post by phoenix1/4 on 2010-10-10
Yep, tried them all. Output after sudo apt-get update is Failed to fetch [archive] Connection failed [IP:127.0.0.1:4567]

---

### Post by sikander3786 on 2010-10-11
> **phoenix1/4 said:**
> Yep, tried them all. Output after sudo apt-get update is Failed to fetch [archive] Connection failed [IP:127.0.0.1:4567]
That absolutely looks like an internet connection problem. You are directly connected to the internet or via proxy server? Internet works without problems in internet browser?

---

