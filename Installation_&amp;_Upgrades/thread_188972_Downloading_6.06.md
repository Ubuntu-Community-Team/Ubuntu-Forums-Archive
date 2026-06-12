---
title: "Downloading 6.06"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by scoot1955 on 2006-06-04
I got the notification for downloading 6.06 and this is what cam up during the download.  Not sure what the heck this means.  Any remedies???
Thanks



Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

---

### Post by az on 2006-06-04
It means those repositories are no longer there.  They don't seem to be official ubuntu repos anyway...

---

### Post by aysiu on 2006-06-04
Dead repositories.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_old
sudo nano /etc/apt/sources.list
``` Delete the offending lines. Save (control-x), confirm (y), exit (Enter).

---

### Post by scoot1955 on 2006-06-10
what the heck does this mean???
I used the code you gave me and this is what I got.  Cornfused  

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as

---

### Post by John.Michael.Kane on 2006-06-10
scoot1955 try replacing your source list.  

```
**sudo gedit /etc/apt/sources.list**

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

**Then run sudo aptitude update**
**Followed by sudo aptitude dist-upgrade**

```

---

### Post by scoot1955 on 2006-06-14
Thanks all.  I just decided to order the cd from unbutu.  I am an almost newbie with this and not really sure of doing anything in terminal.  I have done a few things and it worked out alright but this, to me, is a big step.  Kind of afraid of goofing things up, totally.  I like to take things in stride and making sure of what I am doing.  Learning as I go.  Thanks again.

---

