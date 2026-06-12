---
title: "None-authenticated packages...."
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by BoomAM on 2006-08-03
Hi.
I just ran system update and theres 7 or so updates to things like Firefox & the kernel, however it says that they cant be authenticated. 

Are they going to be safe to use?

Thanks in advance all.  :)

---

### Post by Sutekh on 2006-08-04
Which packages in particular can't be authenticated (shouldn't be the kernel)?

Can you also post your sources, to see where you are getting the packages from?  Use this command from a Terminal window (Applications -> Accessories menu)
```
cat /etc/apt/sources.list
```
In all likeliness there shouldn't be a problem.  Often packages from non-Official Ubuntu repositories aren't digitally signed, so apt-get lists them as un-authenticated.

---

### Post by BoomAM on 2006-08-04
```
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univer                                     se multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted un                                     iverse multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
boomam@boomam-laptop:~$

```

---

### Post by Sutekh on 2006-08-06
Well everything looks pretty standard.  Can you identify what package (s) in particular are not authenticated?  Perhaps something from the multiverse or backports?

---

### Post by BoomAM on 2006-08-06
Strange.
I tryed the update manager again the next day and the warnings went away.
Prehaps the updates it picked up had only just gone on the Ubuntu servers or something?

---

### Post by Sutekh on 2006-08-06
Quite possibly (not that I really know how such things work), or else it really was un-authenticated, until someone fixed that up.

---

### Post by BoomAM on 2006-08-06
Thanks for the help either way though. :)

---

### Post by confused57 on 2006-08-06
> **BoomAM said:**
> Strange.
I tryed the update manager again the next day and the warnings went away.
Prehaps the updates it picked up had only just gone on the Ubuntu servers or something?

I believe authenticated has something to do with public keys(gpg?) for the server, no keys it's designated not-authenticated.  Maybe the keys were somehow installed or recognized on your last try.

---

