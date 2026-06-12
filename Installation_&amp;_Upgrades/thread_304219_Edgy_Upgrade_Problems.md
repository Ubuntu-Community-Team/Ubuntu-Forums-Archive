---
title: "Edgy Upgrade Problems"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by mormonchess on 2006-11-21
I get the following error messages when I attempt to upgrade via the "official" method.

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I have tried repeatedly to upgrade, and this is always the error message I get.  It truly shouldn't be this hard to upgrade.

Anybody have any solutions to this?

---

### Post by taurus on 2006-11-21
Paste your /etc/apt/sources.list here then!

```
cat /etc/apt/sources.list
```
p.s.  What do you mean by the "official" method?

---

### Post by mormonchess on 2006-11-21
Um, the official method listed at the top of the support webpage.....

"Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
Code:

$ gksu "update-manager -c"

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)"

---

### Post by taurus on 2006-11-21
What about your /etc/apt/sources.list???

```
cat /etc/apt/sources.list
```

---

### Post by mormonchess on 2006-11-21
Sorry, here it is:

## Uncomment the following two lines to fetch updated software from the network
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free

---

### Post by taurus on 2006-11-21
Wait a second!  You said that you used the official method to upgrade from Dapper to Edgy but your /etc/apt/sources.list still uses dapper except the second line, CD-ROM!  I think you need to edit it by hand and replace all the dapper with edgy.

Applications -> Accessories -> Terminal

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by mormonchess on 2006-11-21
Ok, I will give that a shot as soon as I get home from work.

Just a question though: why would I have to update this by hand if the official install is used?  Seems kinda "non-automatic" to me.

Please keep in mind that I'm a Linux newbie...I've only been using it for a month and a half, so there is still a lot for me to learn.

---

### Post by taurus on 2006-11-21
It should convert all the dapper to edgy in /etc/apt/sources.list if you were using the official method!  I am not sure why it didn't...

---

### Post by cantormath on 2006-11-21
> **mormonchess said:**
> Um, the official method listed at the top of the support webpage.....

"Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
Code:

$ gksu "update-manager -c"

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)"

Did you read the rest of the posts below that one?

---

### Post by mormonchess on 2006-11-21
Ok I'm starting to get a little frustrated here.

I haven't been told any solution.  I just tried installing Edgy using the "OFFICIAL" method and I get the EXACT SAME error message as I got before.

My Update Manager can't seem to even get the files necessary to install Edgy.

What is the deal???

:mad:

---

