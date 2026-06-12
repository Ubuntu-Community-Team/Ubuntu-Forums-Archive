---
title: "Repository Change"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by Bengaul on 2006-09-16
Hi,

I recently cleaned up my repository list, and have included the code below:

# Specialized Basic Ubuntu Multimedia Preparation Script sources.
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted

## Major Bugfixes
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

## Debian Multimedia Repository
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge main

## Original BUMPS repository.
## deb [http://www.politicalcrossfire.com/ubuntu/dapper](http://www.politicalcrossfire.com/ubuntu/dapper) dapper main non-free
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


When I try an update now, I get this error:

E: /var/cache/apt/archives/libmjpegtools0_1%3a1.8.0-0.3sarge1_i386.deb: trying to overwrite `/usr/lib/libmjpegutils-1.8.so.0.0.0', which is also in package libmjpegtools0c2a

I also get this error:

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

If I run apt-get, I get the same error.

Anyone have any ideas?

Many thanks,

Ben.

---

### Post by whizbaby on 2006-09-16
To your key problem: have you read
[http://www.debian-multimedia.org/faq.html](http://www.debian-multimedia.org/faq.html)
???
EDIT:
The libjpegtools which causes a conflict is a debian sarge package and comes from this repository,too (you can see it here [http://www.debian-multimedia.org/dists/sarge/main/binary-i386/Packages)](http://www.debian-multimedia.org/dists/sarge/main/binary-i386/Packages)).
You will have to check if you really need this repository (I recommend removing the *breezy* entries,too)

---

### Post by Bengaul on 2006-09-16
Ah yes, getting rid of the debian-multimedia repository seems to have done the trick. 

Many thanks for your help.

---

