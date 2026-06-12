---
title: "Clamav install? I'm fed up!!!"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by three-cushion on 2007-01-28
I have tried to install clamav since *forever* after getting Ubuntu running smoothly. 
I bought the HACK book for other references... AND used its approach as follows
```
 sudo apt-get install clamav
```   
That ALWAYS fails b/c <libclamav1> dependency that requires libgmp3 (a virtual file???) 
Then I used ```
 sudo apt-get -f install 
```

That failed as well.
So I tried the following:
```
 sudo aptitude install clamav 
```

That went a little ways, then said I needed to install some 0.88.2 versions of clamav (instead of the current 0.88.7). WHY?? I don;t have a clue.

Here is my /etc/apt/sources.list: sometimes that may limit a good install.upgrade, I'm told
```
 
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://ftp2.de.debian.org/debian-volatile/ sarge/volatile main

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
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted

```

Well I'm stumped. I wish there was a MARK ALLAN who supports clamXav for OS X users on Macs.He gets my donation b/c he produces CLEAR HOWTOs for build, compile & install clamXav . 
Where is such a person for the Ubuntu 6.06 LTS install of clamav? 

I won't run ANY system on the Net w/o an anti-virus. Linux users say it is not needed... sounds like the Mac user community...

Someday.... it will happen.

Thanx to all of you who have tried to help... 

Cheers

==========================================

WHOA... I just installed clamav and scanned my Desktop!!!

HOW?  I replaced my <sources.list> with a CLEAN copy... 
Then did a normal install.

I used avscan and it worked fine...


N O W ... I have to install an updated engine.... I have the source for that... will try again tomorrow...

Sorry for my ranting above... The Ubuntu Hacks book helped a lot...as well as this forum.

Cheers

---

### Post by three-cushion on 2007-01-31
After studying the forum and the "---Hacks" book, I now have a clamav installed and scanning (manually).

Now I need to update to the 0.88.7 version. I downloaded from the clamav site... now How do I install it? This is not a "package" just a dir of files.

It's got to be simple... but it's not obvious.

The version from the Universe repos is 0.88.4,,, so synaptic says we're up to date... Hmmm..

A little help when you have time... Thanx
Jim B

---

### Post by johnnydepp74 on 2007-02-23
Peace Bro,

Hope this helps..

First create a user called clamav and a group called clamav. Next,

1) download  clam.0.88.7.tar.gz to your download folder
2) tar -xzvf clam.0.88.7.tar.gz
3) cd clam0.88.7
4) ./configure --with-user=clamav (by defa, it looks for user "clamav" if dun specify --with-user)
5) sudo make
6) sudo make install

whatever error message you get like missing this file, that file during configure, please install those missing ones first.

Next time, if u want to remove the old clamav version, just do a make uninstall and repat steps 1 - 6 again for the new version.

Cheers
John Singapore

---

