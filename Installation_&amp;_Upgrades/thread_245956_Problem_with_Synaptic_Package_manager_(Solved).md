---
title: "Problem with Synaptic Package manager (Solved)"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by carltonx on 2006-08-28
I was adding this Channel to the Manager so that I could download Real Player
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main. now there is nothing in the manager instead I get this error message.

E: Malformed line 38 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I went to command line and typed "gksu gedit /etc/apt/sources.list" this the result. I cant see naything wrong soplease help me.
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)

This also appeared in the command box after the list.carlton@ubuntu:~$ gksu gedit /etc/apt/sources.list
(gedit:5520): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


I will appreaciate any help.

---

### Post by aysiu on 2006-08-28
These are the malformed lines: ```
deb http://archive.canonical.com/ubuntu
deb http://archive.canonical.com/ubuntu
``` Notice how all the other lines have a couple of words after the web address?

Get a fresh list here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by carltonx on 2006-08-28
carlton@ubuntu:~$ sudo cp /etc/apt/sources.list etc/apt/sources.list_backupgksudo gedit /etc/apt/sources.list
cp: target `/etc/apt/sources.list' is not a directory
carlton@ubuntu:~$

I went to the site you posted and the above result is what I got after typing in the informatiom they gave. So it did not work.

---

### Post by Leif on 2006-08-28
That's two separate commands, carltonx.

First :
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```
which backs up your original list, in case you want to revert at some point.

Second :
```

gksudo gedit /etc/apt/sources.list

```

---

### Post by carltonx on 2006-08-31
Thank you leif it w0rked :p

---

### Post by roshanali on 2006-11-01
thanks so much.i was having a similiar problem with the synaptic packege manager and this solution worked.
thanks again:D :D

---

