---
title: "where's pidgin?"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by razorednight on 2007-08-31
I keep seeing stuff about pidgin on these forums, but I search for it in Synaptic and nothing turns up.  I've got all the repos I think.  Here's my sources.list:

```
martin@x-box:~$ cat /etc/apt/sources.list
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free 

martin@x-box:~$ 

```

Can anyone tell me where I can find pidgin?

---

### Post by bapoumba on 2007-08-31
It's not in the feisty repos. I have not read the whole thread I'm linking:
[http://ubuntuforums.org/showthread.php?t=404508]("http://ubuntuforums.org/showthread.php?t=404508")

Edit: from above thread, Getdeb has a package:
[http://www.getdeb.net/release.php?id=1307]("http://www.getdeb.net/release.php?id=1307")

---

### Post by razorednight on 2007-08-31
Oh I see!  That says it's a Beta, and it's got to be compiled... that's not how I thought it was at all!

Thanks for the link bapoumba!  I think I'll stick with gaim for now.

---

### Post by bapoumba on 2007-08-31
You're welcome :)
It's in gusty, so you'll have it soon if you upgrade when gutsy comes out.

---

