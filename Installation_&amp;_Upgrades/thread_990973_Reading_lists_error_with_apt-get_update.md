---
title: "Reading lists error with apt-get update"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by harsha10 on 2008-11-23
Hi all
I am using Ubuntu 8.10.
Recently i did some update and during installation of updates i did something wrong ( i don't remember exactly )
Next time when i ran this command i got the following error please help me

```


prashant@CluTch:~$ sudo apt-get update
Reading package lists... Error!
E: Read error - read (21 Is a directory)
E: The package lists or status file could not be parsed or opened.
prashant@CluTch:~$ 


```

Waiting for reply ...
Please help me ...( Urgent ..)

---

### Post by harsha10 on 2008-11-23
When i ran dpkg --configure -a i got the following 

```


prashant@CluTch:~$ sudo dpkg --configure -a
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Is a directory
prashant@CluTch:~$ 


```

Please help me ...
With regards

---

### Post by harsha10 on 2008-11-23
My apt-sources.list is as follows :- 

```


prashant@CluTch:~$ cat /etc/apt/sources.list
 #deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081030)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb-src http://in.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiversedeb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiversedeb http://archive.ubuntu.com/ubuntu gutsy universe multiverse
 deb-src http://archive.ubuntu.com/ubuntu gutsy universe multiverse

# PPA lauchpad 
deb http://ppa.launchpad.net/wouterh/ubuntu intrepid main
prashant@CluTch:~$ 


```

Waiting for reply ....

---

